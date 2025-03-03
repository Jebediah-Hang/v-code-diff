<script setup lang="ts">
import { computed, ref, watch } from 'vue-demi'
import { createSplitDiff, createUnifiedDiff } from './utils'
import { SplitViewerChange, DiffType } from './types'
import UnifiedViewer from './unified/UnifiedViewer.vue'
import SplitViewer from './split/SplitViewer.vue'

import './style.scss'

interface Props {
  newString: string
  oldString: string
  language?: string
  context?: number
  diffStyle?: 'word' | 'char'
  outputFormat?: 'line-by-line' | 'side-by-side'
  trim?: boolean
  noDiffLineFeed?: boolean
  maxHeight?: string
  filename?: string
  newFilename?: string
  hideHeader?: boolean
  hideStat?: boolean
  theme?: 'light' | 'dark'
  // Give a pattern to ignore matching lines eg: '(time|token)'
  ignoreMatchingLines?: string
}

const props = withDefaults(defineProps<Props>(), {
  language: 'plaintext',
  context: 10,
  diffStyle: 'word',
  outputFormat: 'line-by-line',
  trim: false,
  noDiffLineFeed: false,
  maxHeight: undefined,
  filename: undefined,
  newFilename: undefined,
  hideHeader: false,
  hideStat: false,
  theme: 'light',
  ignoreMatchingLines: undefined,
})

const emits = defineEmits<{
  (e: 'diff', diffResult: DiffResult): void
}>()

interface ChangeStat {
  equalCont: number
  onlyCont: number
  changeCont: number
  ignoreCont: number
}

interface DiffResult {
  diffChange: Array<number>,
  stat: ChangeStat
}

const isUnifiedViewer = computed(() => props.outputFormat === 'line-by-line')

const oldString = computed(() => {
  let value = props.oldString || ''
  value = props.trim ? value.trim() : value
  value = props.noDiffLineFeed ? value.replace(/(\r\n)/g, '\n') : value
  return value
})
const newString = computed(() => {
  let value = props.newString || ''
  value = props.trim ? value.trim() : value
  value = props.noDiffLineFeed ? value.replace(/(\r\n)/g, '\n') : value
  return value
})

const raw = computed(() =>
  isUnifiedViewer.value
    ? createUnifiedDiff(oldString.value, newString.value, props.language, props.diffStyle, props.context, props.ignoreMatchingLines)
    : createSplitDiff(oldString.value, newString.value, props.language, props.diffStyle, props.context, props.ignoreMatchingLines),
)
const diffChange = ref(raw.value)
// const isNotChanged = computed(() => diffChange.value.stat.additionsNum === 0 && diffChange.value.stat.deletionsNum === 0)

const splitDiffViewer = ref<InstanceType<typeof SplitViewer> | null>(null)

function jumpToChange(line: number) {
  splitDiffViewer.value?.jumpToChange(line)
}

defineExpose({
  jumpToChange
})

watch(() => props, () => {
  diffChange.value = raw.value
  const statistic: ChangeStat = {
    equalCont: 0,
    onlyCont: 0,
    changeCont: 0,
    ignoreCont: 0
  }
  const changedList: Array<number> = []
  if (!isUnifiedViewer.value) {
    let cStat = false
    const { changes } = <SplitViewerChange>diffChange.value
    for (let i = 0; i < changes.length; i++) {
      const { left: { type: lType }, right: { type: rType } } = changes[i]
      if (lType === DiffType.EQUAL && rType === DiffType.EQUAL) {
        // 两边都是equal的算相同的行
        statistic.equalCont++
      } else if (
        (lType === DiffType.IGNORE && rType != DiffType.EMPTY) ||
        (lType != DiffType.EMPTY && rType === DiffType.IGNORE)
      ) {
        // 一边是ignore，另一边不为empty的，算忽略，并加到相同里面
        statistic.ignoreCont++
        statistic.equalCont++
      } else if (lType === DiffType.DELETE && rType === DiffType.ADD) {
        // 左边delete右边add的算改变的行
        statistic.changeCont++
      } else {
        // 其他的全算唯一的行
        statistic.onlyCont++
      }
      // 统计变更块
      if (!cStat && lType !== rType) {
        changedList.push(i)
        cStat = true
      }
      if (cStat && lType === rType) {
        cStat = false
      }
    }
  }
  console.log('diffchange--', diffChange.value)
  emits('diff', {
    diffChange: changedList,
    stat: statistic
  })
}, { deep: true, immediate: true })
</script>

<template>
  <div class="code-diff-view" :theme="theme" :style="{ maxHeight }">
    <div v-if="!hideHeader" class="file-header">
      <!--  line by line -->
      <div v-if="isUnifiedViewer" class="file-info">
        <span>
          <div class="info-left">{{ filename }}</div>
          <div class="info-left">{{ newFilename }}</div>
        </span>
        <span v-if="!hideStat" class="diff-stat">
          <slot name="stat" :stat="diffChange.stat">
            <span class="diff-stat-added">+{{ diffChange.stat.additionsNum }} additions</span>
            <span class="diff-stat-deleted">-{{ diffChange.stat.deletionsNum }} deletions</span>
          </slot>
        </span>
      </div>
      <!-- side by side -->
      <div v-else class="file-info">
        <span class="info-left">{{ filename }}</span>
        <span class="info-right">
          <span style="margin-left: 20px;">{{ newFilename }}</span>
          <span v-if="!hideStat" class="diff-stat">
            <slot name="stat" :stat="diffChange.stat">
              <span class="diff-stat-added">+{{ diffChange.stat.additionsNum }} additions</span>
              <span class="diff-stat-deleted">-{{ diffChange.stat.deletionsNum }} deletions</span>
            </slot>
          </span>
        </span>
      </div>
    </div>
    <UnifiedViewer v-if="isUnifiedViewer" :diff-change="diffChange" />
    <SplitViewer v-else ref="splitDiffViewer" :diff-change="diffChange" :context="context" />
  </div>
</template>

<style lang="scss">
</style>

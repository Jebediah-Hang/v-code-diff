<script setup lang="ts">
import { ref } from 'vue-demi';
import type { SplitLineChange, SplitViewerChange } from '../types'
import SplitLine from './SplitLine.vue'

const props = defineProps<{
  diffChange: SplitViewerChange,
  context: number
}>()

function expandHandler({ hideIndex }: SplitLineChange) {
  if (hideIndex === undefined)
    return
  props.diffChange.collector[hideIndex!].lines.forEach((line) => {
    line.hide = false
    line.fold = false
  })
}

const splitViewEl = ref<HTMLElement | null>(null)

function jumpToChange(line: number) {
  const lineEl = splitViewEl.value?.children[line]
  lineEl && lineEl.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

defineExpose({
  jumpToChange
})

</script>

<template>
  <table class="file-diff-split diff-table">
    <colgroup>
      <col width="44">
      <col>
      <col width="44">
      <col>
    </colgroup>
    <tbody ref="splitViewEl">
      <SplitLine
        v-for="(item, index) in diffChange?.changes"
        :key="index"
        :split-line="item"
        :context="context"
        @expand="expandHandler"
      />
    </tbody>
  </table>
</template>

<style scoped></style>

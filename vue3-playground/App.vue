<script lang="ts" setup>
import { version } from 'vue-demi'
import { reactive } from 'vue'

// import { oldLongText } from '../demo/text/old-long-text'
// import { newLongText } from '../demo/text/new-long-text'

const form = reactive({
  // oldString: oldLongText,
  // newString: newLongText,
  oldString: '{\n  "code": "200",\n  "msg": "请求成功",\n  "data": {\n    "hitokoto": "往者不可谏，来者犹可追。",\n    "from": "论语·微子篇"\n  },\n  "time": "2024-01-12 17:27:03"\n}',
  newString: '{\n  "code": "200",\n  "msg": "请求成功",\n  "data": {\n    "hitokoto": "成熟的人眼里满是前途，稚嫩的人眼里满是爱恨情仇。",\n    "from": "网易云热评"\n  },\n  "time": "2024-01-12 17:27:06"\n}',
  filename: 'oldFile',
  newFilename: 'newFile',
  language: 'json',
  diffStyle: 'word',
  outputFormat: 'side-by-side',
  ignoreMatchingLines: 'time',
  context: 3,
})
</script>

<template>
  <p align="center">
    Vue version: {{ version }}
  </p>
  <div style="display: flex; justify-content: space-evenly">
    <textarea v-model="form.oldString" style="width: 48vw;" :rows="20" />
    <textarea v-model="form.newString" style="width: 48vw;" :rows="20" />
  </div>
  <CodeDiff
    :old-string="form.oldString"
    :new-string="form.newString"
    :filename="form.filename"
    :new-filename="form.newFilename"
    :language="form.language"
    :output-format="form.outputFormat"
    :ignore-matching-lines="form.ignoreMatchingLines"
    :diff-style="form.diffStyle"
    :context="form.context"
  />
</template>

<style>
body > div {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #2c3e50;
}
</style>

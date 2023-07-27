<script setup lang="ts">
import { reactive } from 'vue'
import Counter from './components/Counter.vue'

interface AppInfo {
  name: string
  slogan: string
}

const appInfo: AppInfo = reactive({
  name: 'TS Counter',
  slogan: 'Learning TS',
})
</script>

<template>
  <h1>{{ appInfo.name }}</h1>
  <h2>{{ appInfo.slogan }}</h2>
  <Counter :limit="5" />
</template>

<style scoped></style>

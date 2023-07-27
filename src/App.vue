<script setup lang="ts">
import { onMounted, reactive, ref } from 'vue'
import fetchCount from './fetchCount'

interface AppInfo {
  name: string
  slogan: string
}

const count = ref<number | null>(null)

const appInfo: AppInfo = reactive({
  name: 'TS Counter',
  slogan: 'Learning TS',
})

onMounted(() => {
  fetchCount((initCount) => {
    count.value = initCount
  })
})
</script>

<template>
  <h1>{{ appInfo.name }}</h1>
  <h2>{{ appInfo.slogan }}</h2>
  <p>{{ count }}</p>
</template>

<style scoped></style>

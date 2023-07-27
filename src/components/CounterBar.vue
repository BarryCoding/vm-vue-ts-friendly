<script setup lang="ts">
const emit = defineEmits<{
  addCount: [num: number]
  reset: []
}>()
</script>

<template>
  <button @click="emit('addCount', 1)" :style="{ marginRight: '10px' }">
    Add
  </button>
  <button @click="emit('reset')">Reset</button>
</template>

<style scoped></style>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
import fetchCount from '../fetchCount'
import CounterBar from './CounterBar.vue'

interface Props {
  limit: number
  alertMessageOnLimit?: string
}

const props = withDefaults(defineProps<Props>(), {
  alertMessageOnLimit: 'you have reached the counter limit',
})

const count = ref<number | null>(null)

const addCount = (num: number) => {
  if (!count.value) return

  if (count.value >= props.limit) {
    return alert(props.alertMessageOnLimit)
  }

  count.value = count.value + num
}

onMounted(() => {
  fetchCount((initCount) => {
    count.value = initCount
  })
})
</script>

<template>
  <p>{{ count }}</p>
  <CounterBar @addCount="addCount" @reset="count = 0" />
</template>

<style scoped></style>

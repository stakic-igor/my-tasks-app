<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'

const props = defineProps<{
  list: MyTasks
}>()
</script>

<template>
  <h1>task item</h1>
  <p>{{ list.title }}</p>
  <p>{{ list.description }}</p>
  <p>{{ list.completed }}</p>
</template>

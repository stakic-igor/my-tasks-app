<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'

const props = defineProps<{
  list: MyTasks
}>()

const emit = defineEmits<{
  deleteTask: [id: number]
}>()
</script>

<template>
  <h1>task item</h1>
  <p>{{ list.id }} - {{ list.title }}</p>
  <p>{{ list.description }}</p>
  <p>{{ list.completed }}</p>
  <button @click="$emit('deleteTask', list.id)">Delete</button>
</template>

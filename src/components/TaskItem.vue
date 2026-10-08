<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'

const props = defineProps<{
  list: MyTasks
}>()

const emit = defineEmits<{
  deleteTask: [id: number]
  completedTask: [id: number]
}>()
</script>

<template>
  <p>{{ list.id }} - {{ list.title }}</p>
  <p>{{ list.description }}</p>
  <p>{{ list.completed }}</p>
  <input type="checkbox" :checked="list.completed" @change="$emit('completedTask', list.id)" />
  <button @click="$emit('deleteTask', list.id)">Delete</button>
</template>

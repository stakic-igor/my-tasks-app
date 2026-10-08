<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'
import TaskItem from '@/components/TaskItem.vue'

const props = defineProps<{
  tasks: MyTasks[]
}>()

const emit = defineEmits<{
  deleteTask: [id: number]
}>()

const handleTaskDelete = (id: number) => {
  emit('deleteTask', id)
}
</script>
<template>
  <h1>Todo List</h1>
  <TaskItem v-for="item in tasks" :key="item.id" :list="item" @delete-task="handleTaskDelete" />
</template>

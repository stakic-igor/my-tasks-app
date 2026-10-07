<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'
import TaskItem from '@/views/TaskItem.vue'

const props = defineProps<{
  tasks: MyTasks[]
}>()
</script>
<template>
  <h1>Todo List</h1>
  <TaskItem v-for="item in tasks" :key="item.id" :list="item" />
</template>

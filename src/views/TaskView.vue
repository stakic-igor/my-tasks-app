<script setup lang="ts">
import { ref } from 'vue'
import type { MyTasks } from '@/types/task-list.ts'
import TaskList from '../components/TaskList.vue'

const myTasks = ref<MyTasks[]>([
  { id: 1, title: 'Get up', description: 'Get ready to learn and work', completed: false },
  { id: 2, title: 'Suplements', description: 'Take suplements', completed: false },
  { id: 3, title: 'First practice project', description: 'Complete task app', completed: true },
])
</script>
<template>
  <h1>Task View</h1>
  <TaskList :tasks="myTasks" />
</template>

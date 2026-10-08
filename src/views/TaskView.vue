<script setup lang="ts">
import { ref } from 'vue'
import type { MyTasks } from '@/types/task-list.ts'
import TaskList from '../components/TaskList.vue'
import TaskForm from '@/components/TaskForm.vue'

const myTasks = ref<MyTasks[]>([
  { id: 1, title: 'Get up', description: 'Get ready to learn and work', completed: false },
  { id: 2, title: 'Suplements', description: 'Take suplements', completed: false },
  { id: 3, title: 'First practice project', description: 'Complete task app', completed: true },
])

const executeTaskDelete = (id: number) => {
  myTasks.value = myTasks.value.filter((item) => item.id != id)
}
</script>
<template>
  <h1>Task View</h1>
  <TaskForm />
  <TaskList :tasks="myTasks" @delete-task="executeTaskDelete" />
</template>

<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'
import TaskItem from '@/components/TaskItem.vue'

const props = defineProps<{
  tasks: MyTasks[]
}>()

const emit = defineEmits<{
  deleteTask: [id: number]
  completedTask: [id: number]
}>()

const handleTaskDelete = (id: number) => {
  emit('deleteTask', id)
}

const handleCompletedTask = (id: number) => {
  emit('completedTask', id)
}
</script>
<template>
  <div>
    <TaskItem
      v-for="item in tasks"
      :key="item.id"
      :list="item"
      @completed-task="handleCompletedTask"
      @delete-task="handleTaskDelete"
    />
  </div>
</template>

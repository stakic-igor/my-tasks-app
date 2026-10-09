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
  <section class="p-2 rounded-md bg-gray-200 mb-2 last:mb-0">
    <div class="flex flex-row gap-2 items-start">
      <input
        type="checkbox"
        class="w-4 h-4 mt-1 border-0 rounded-sm bg-white checked:bg-blue-500 cursor-pointer"
        :checked="list.completed"
        @change="$emit('completedTask', list.id)"
      />
      <p class="font-medium" :class="list.completed ? 'line-through' : ''">
        {{ list.title }}
      </p>
    </div>
    <p class="text-sm font-light mt-2">{{ list.description }}</p>
    <div class="mt-2">
      <button
        class="bg-red-500 text-white text-xs font-light cursor-pointer rounded-full px-2 py-0.5 min-w-16 text-center"
        @click="$emit('deleteTask', list.id)"
      >
        Delete
      </button>
    </div>
  </section>
</template>

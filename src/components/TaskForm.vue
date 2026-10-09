<script setup lang="ts">
import { ref } from 'vue'

const taskTitle = ref('')
const taskDescription = ref('')

const emit = defineEmits<{
  'add-task': [taskTitle: string, taskDescription: string]
}>()

const handleSubmit = () => {
  emit('add-task', taskTitle.value, taskDescription.value)
  taskTitle.value = ''
  taskDescription.value = ''
}
</script>

<template>
  <section class="max-w-120">
    <form @submit.prevent="handleSubmit" class="flex flex-col gap-2">
      <div>
        <label for="task-title" class="block font-light mb-1 focus:outline-none">Task title</label>
        <input
          type="text"
          id="task-title"
          v-model="taskTitle"
          placeholder="task title"
          autocomplete="off"
          class="border-0 p-1 rounded bg-gray-100 w-full"
          required
        />
      </div>
      <div>
        <label for="task-description" class="block font-light mb-1">Task description</label>
        <textarea
          id="task-description"
          v-model="taskDescription"
          placeholder="task description"
          class="border-0 p-1 rounded bg-gray-100 w-full"
          required
        ></textarea>
      </div>
      <button
        type="submit"
        class="rounded bg-blue-500 text-white px-4 py-2 cursor-pointer self-end"
      >
        Add task
      </button>
    </form>
  </section>
</template>

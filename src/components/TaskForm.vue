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
  <section>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="task-title">Task title</label>
        <input type="text" id="task-title" v-model="taskTitle" class="border" required />
      </div>
      <div>
        <label for="task-description">Task description</label>
        <textarea
          id="task-description"
          v-model="taskDescription"
          class="border"
          required
        ></textarea>
      </div>
      <button type="submit">Add task</button>
    </form>
  </section>
</template>

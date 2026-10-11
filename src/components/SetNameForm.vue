<script setup lang="ts">
import { ref } from 'vue'

const name = ref('')

const props = defineProps<{
  isNameFormVisible: boolean
}>()

const emit = defineEmits<{
  'set-name': [name: string]
}>()

const handleSubmit = () => {
  const trimmedName = name.value.trim()
  if (!trimmedName) return

  emit('set-name', trimmedName)
  name.value = trimmedName
}
</script>

<template>
  <form @submit.prevent="handleSubmit" :class="isNameFormVisible ? 'block' : 'hidden'">
    <label for="name" class="block font-light text-xs mb-1 focus:outline-none">Name:</label>
    <div class="flex flex-row gap-2">
      <input
        type="text"
        id="name"
        name="name"
        v-model="name"
        required
        class="border border-[#F4F4F4] px-2 py-1 rounded-lg bg-[#F9F9F9] w-full"
      />
      <button type="submit" class="rounded-lg bg-green-600 text-white px-2 py-1 cursor-pointer">
        Save
      </button>
    </div>
  </form>
</template>

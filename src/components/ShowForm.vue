<script setup lang="ts">
import PlusIcon from '@/icons/PlusIcon.vue'

const emit = defineEmits<{
  'show-form': []
}>()
</script>
<template>
  <button class="w-7 h-7 cursor-pointer" @click="$emit('show-form')">
    <PlusIcon />
  </button>
</template>

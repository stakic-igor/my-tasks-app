<script setup lang="ts">
const props = defineProps<{
  active: number
  completed: number
}>()
</script>

<template>
  <div>{{ active }} active | {{ completed }}completed</div>
</template>

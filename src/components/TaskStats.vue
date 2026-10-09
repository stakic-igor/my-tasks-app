<script setup lang="ts">
const props = defineProps<{
  active: number
  completed: number
}>()
</script>

<template>
  <section class="flex row gap-2 align-middle justify-center mt-2">
    <span class="font-light text-xs">{{ active }} active | {{ completed }} completed</span>
  </section>
</template>

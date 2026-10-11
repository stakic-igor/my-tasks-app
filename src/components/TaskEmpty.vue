<script setup lang="ts">
defineProps<{ message: string }>()
</script>

<template>
  <section class="flex flex-col items-center justify-center rounded-2xl p-2 mt-4 bg-[#F9F9F9] h-32">
    <p class="my-2">{{ message }}</p>
    <slot />
  </section>
</template>

<script setup lang="ts">
import type { taskFilter } from '@/types/task-filters.ts'

const props = defineProps<{
  filters: taskFilter
}>()

const emit = defineEmits<{
  'update:filters': [filter: taskFilter]
}>()
</script>

<template>
  <section class="flex row gap-2 align-middle justify-center">
    <label
      for="all"
      class="border-2 rounded-full px-2 py-1 min-w-16 text-center cursor-pointer has-checked:border-blue-500"
    >
      <input
        type="radio"
        id="all"
        name="filter"
        value="all"
        :checked="props.filters === 'all'"
        @change="emit('update:filters', 'all')"
        class="mr-2 hidden"
      />
      <span>All</span>
    </label>
    <label for="active" class="border-2 rounded-full px-2 py-1 min-w-16 text-center cursor-pointer">
      <input
        type="radio"
        id="active"
        name="filter"
        value="active"
        :checked="props.filters === 'active'"
        @change="emit('update:filters', 'active')"
        class="mr-2 hidden"
      />
      <span>Active</span>
    </label>
    <label
      for="completed"
      class="border-2 rounded-full px-2 py-1 min-w-16 text-center cursor-pointer"
    >
      <input
        type="radio"
        id="completed"
        name="filter"
        value="completed"
        :checked="props.filters === 'completed'"
        @change="emit('update:filters', 'completed')"
        class="mr-2 hidden"
      />
      <span>Completed</span>
    </label>
  </section>
</template>

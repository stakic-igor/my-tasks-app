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
  <section>
    <label for="all">
      <input
        type="radio"
        id="all"
        name="filter"
        value="all"
        :checked="props.filters === 'all'"
        @change="emit('update:filters', 'all')"
      />
      <span>All</span>
    </label>
    <label for="active">
      <input
        type="radio"
        id="active"
        name="filter"
        value="active"
        :checked="props.filters === 'active'"
        @change="emit('update:filters', 'active')"
      />
      <span>Active</span>
    </label>
    <label for="completed">
      <input
        type="radio"
        id="completed"
        name="filter"
        value="completed"
        :checked="props.filters === 'completed'"
        @change="emit('update:filters', 'completed')"
      />
      <span>Completed</span>
    </label>
  </section>
</template>

<script setup lang="ts">
import type { MyTasks } from '@/types/task-list.ts'
import CheckedRoundFilledIcon from '@/icons/CheckedRoundFilledIcon.vue'
import CheckedRoundIcon from '@/icons/CheckedRoundIcon.vue'
import RecycleBinIcon from '@/icons/RecycleBinIcon.vue'

const props = defineProps<{
  list: MyTasks
}>()

const emit = defineEmits<{
  deleteTask: [id: number]
  completedTask: [id: number]
}>()
</script>

<template>
  <section
    class="group flex flex-row pl-2 rounded-lg border border-[#F8F8F8] mb-2 last:mb-0 mt-4 overflow-hidden relative"
  >
    <div class="flex flex-col gap-2 items-start pt-2 pb-2 grow">
      <p class="font-medium" :class="list.completed ? 'line-through' : ''">
        {{ list.title }}
      </p>
      <p class="text-sm font-light mt-2">{{ list.description }}</p>
    </div>
    <div
      class="group-hover:right-0 group-hover:shadow-[-3px_0_5px_-3px_rgba(0,0,0,0.15)] transition-all duration-200 bg-[#F8F8F8] absolute -right-8 top-0 h-full"
    >
      <label class="cursor-pointer w-8 h-8 flex items-center justify-center hover:bg-[#F5F5F5]">
        <input
          type="checkbox"
          class="peer sr-only"
          :checked="list.completed"
          @change="$emit('completedTask', list.id)"
        />
        <span class="peer-focus-visible:outline">
          <CheckedRoundFilledIcon v-if="list.completed" class="w-4 h-4 text-green-600" />
          <CheckedRoundIcon v-else class="w-4 h-4 text-green-600" />
        </span>
      </label>
      <button
        class="cursor-pointer w-8 h-8 flex items-center justify-center hover:bg-[#F5F5F5]"
        @click="$emit('deleteTask', list.id)"
      >
        <RecycleBinIcon class="text-red-500 w-4 h-auto" />
      </button>
    </div>
  </section>
</template>

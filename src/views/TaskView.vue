<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import type { MyTasks } from '@/types/task-list.ts'
import type { taskFilter } from '@/types/task-filters.ts'
import TaskList from '../components/TaskList.vue'
import TaskForm from '@/components/TaskForm.vue'
import TaskStats from '@/components/TaskStats.vue'
import TaskFilter from '@/components/TaskFilter.vue'
import TaskEmpty from '@/components/TaskEmpty.vue'
import ShowForm from '@/components/ShowForm.vue'
import SetNameForm from '@/components/SetNameForm.vue'
import EditIcon from '@/icons/EditIcon.vue'

const myTasks = ref<MyTasks[]>([])

onMounted(() => {
  const tasks = localStorage.getItem('tasks')
  const name = localStorage.getItem('name')
  if (tasks) {
    myTasks.value = JSON.parse(tasks)
  }
  if (name) {
    myName.value = name
  }
})
const executeTaskDelete = (id: number) => {
  myTasks.value = myTasks.value.filter((item) => item.id !== id)
  localStorage.setItem('tasks', JSON.stringify(myTasks.value))
}

const completedCount = computed(() => {
  return myTasks.value.reduce((sum, item) => sum + (item.completed ? 1 : 0), 0)
})

const activeCount = computed(() => {
  return myTasks.value.reduce((sum, item) => sum + (item.completed ? 0 : 1), 0)
})

const executeCompletedTask = (id: number) => {
  const task = myTasks.value.find((item) => item.id === id)
  if (task) {
    task.completed = !task.completed
  }
  localStorage.setItem('tasks', JSON.stringify(myTasks.value))
}

const filtered = ref<taskFilter>('all')

const visibleTasks = computed(() => {
  if (filtered.value === 'all') {
    return myTasks.value
  }

  return myTasks.value.filter((task) =>
    filtered.value === 'active' ? !task.completed : task.completed,
  )
})

const generateId = () => {
  return Date.now()
}

const getData = (taskTitle: string, taskDescription: string) => {
  myTasks.value.push({
    id: generateId(),
    title: taskTitle,
    description: taskDescription,
    completed: false,
  })
  localStorage.setItem('tasks', JSON.stringify(myTasks.value))
  isFormVisible.value = false
}

const isFormVisible = ref(false)

const showForm = () => {
  isFormVisible.value = true
}

const emptyMessage = computed(() => {
  if (myTasks.value.length === 0) return 'No tasks yet.'
  if (filtered.value === 'active') return 'No active tasks.'
  return 'No completed tasks yet.'
})

const isNameFormVisible = ref(false)

const toggleNameForm = () => {
  isNameFormVisible.value = !isFormVisible.value
}

const myName = ref('')

const addName = (name: string) => {
  myName.value = name
  localStorage.setItem('name', myName.value)
  isNameFormVisible.value = false
}
</script>
<template>
  <main class="mx-auto max-w-90 p-4 bg-[#FEFEFE] rounded shadow mt-32">
    <section class="flex justify-between items-center">
      <p class="font-light text-xs">
        Welcome, <span v-if="myName">{{ myName }}</span
        ><span v-else>Smart One</span>
      </p>
      <button class="h-6 w-6 cursor-pointer" @click="toggleNameForm">
        <EditIcon class="text-black" />
      </button>
    </section>
    <SetNameForm @set-name="addName" :isNameFormVisible="isNameFormVisible" />
    <div class="flex justify-between items-center">
      <h1 class="text-2xl font-bold mb-4">My Tasks</h1>
      <ShowForm @show-form="showForm" />
    </div>
    <div class="flex flex-row">
      <TaskFilter v-model:filters="filtered" />
    </div>
    <TaskList
      v-if="visibleTasks.length > 0"
      :tasks="visibleTasks"
      @delete-task="executeTaskDelete"
      @completed-task="executeCompletedTask"
    />
    <TaskEmpty v-else :message="emptyMessage">
      <ShowForm @show-form="showForm" />
    </TaskEmpty>
    <TaskForm @add-task="getData" :isFormVisible="isFormVisible" />
    <TaskStats :active="activeCount" :completed="completedCount" />
  </main>
</template>

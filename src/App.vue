<script setup>
import TaskTimer from './components/TaskTimer.vue';
import { useTimeStore } from '@/stores/timerStore';

const store = useTimeStore();
</script>
<template>
  <div class="p-6 max-w-3xl mx-auto bg-white shadow-lg rounded-lg">
    <h1 class="text-3xl font-bold text-center text-blue-700 mb-6">⏳ Vue 3 + Vite + Tailwind CSS + Pinia Time Tracker</h1>
    <TaskTimer />
    <div class="mt-10">
      <h2 class="text-xl font-semibold text-gray-800 mb-3">📋 Past Tasks</h2>
      <ul class="space-y-2">
        <li
          v-for="(task, index) in store.tasks"
          :key="index"
          class="bg-gray-50 p-4 rounded border border-gray-200 shadow-sm flex items-center justify-between"
        >
          <div>
            <p class="font-medium text-gray-900">{{ task.name }}</p>
            <p class="text-sm text-gray-600">
              ⏱️ {{ Math.floor(task.duration / 60) }}m {{ task.duration % 60 }}s
            </p>
          </div>
          <span
            v-if="task.status === 'in-progress'"
            class="text-sm text-green-600 font-semibold animate-pulse"
          >
            In Progress...
          </span>
          <span
            v-else-if="task.status === 'paused'"
            class="text-sm text-yellow-500 font-semibold"
          >
            Paused
          </span>
          <span
            v-else-if="task.status === 'completed'"
            class="text-sm text-gray-500 font-semibold"
          >
            Completed
          </span>
        </li>
      </ul>
      <div class="mt-6 bg-gray-100 p-4 rounded text-gray-800">
        <p><strong>Total Tasks:</strong> {{ store.taskCount }}</p>
        <p><strong>Total Time Spent:</strong> {{ Math.floor(store.totalTimeSpent / 60) }}m {{ store.totalTimeSpent % 60 }}s</p>
      </div>
      <button
        class="mt-6 px-6 py-2 bg-red-600 hover:bg-red-500 text-white rounded shadow-md transition"
        @click="store.clearAllTasks()"
      >
        🗑️ Clear All Tasks
      </button>
    </div>
  </div>
</template>

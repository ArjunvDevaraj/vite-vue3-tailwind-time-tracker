<script setup>
import { ref, watchEffect } from 'vue';
import { useTimeStore } from '@/stores/timerStore';

const taskName = ref('');
const store = useTimeStore();

const start = () => {
  if (taskName.value.trim()) {
    store.startTask(taskName.value);
  }
};

const pauseResume = () => {
  if (store.isPaused) {
    store.resumeTask();
  } else {
    store.pauseTask();
  }
};

const stop = () => {
  store.stopTask();
};

const timer = ref(0);

watchEffect(() => {
  timer.value = store.timer;
});
</script>


<template>
  <div class="task-timer p-4 bg-white rounded shadow space-y-4">
    <input
      v-model="taskName"
      type="text"
      placeholder="Enter task name..."
      class="w-full border border-gray-300 px-4 py-2 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
    />
    <div class="flex gap-4">
      <button
        @click="start"
        :disabled="store.currentTask"
        class="flex-1 bg-green-500 hover:bg-green-600 text-white font-semibold py-2 px-4 rounded transition duration-200 disabled:opacity-50"
      >
        Start
      </button>
      <button
        @click="pauseResume"
        :disabled="!store.currentTask"
        class="flex-1 bg-yellow-500 hover:bg-yellow-600 text-white font-semibold py-2 px-4 rounded transition duration-200 disabled:opacity-50"
      >
        {{ store.isPaused ? 'Resume' : 'Pause' }}
      </button>
      <button
        @click="stop"
        :disabled="!store.currentTask"
        class="flex-1 bg-red-500 hover:bg-red-600 text-white font-semibold py-2 px-4 rounded transition duration-200 disabled:opacity-50"
      >
        Stop
      </button>
    </div>
    <div class="mt-6 text-center">
      <div v-if="store.currentTask" class="inline-flex items-center gap-2 text-green-600 text-lg font-medium animate-pulse">
        <svg class="w-5 h-5 animate-spin" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v4m0 8v4m8-8h-4m-8 0H4m15.36 6.36l-2.83-2.83M6.34 6.34L9.17 9.17m0 5.66l-2.83 2.83m11.31-11.31l-2.83 2.83" />
        </svg>
        Task In Progress...
      </div>
      <div v-else class="text-gray-600 text-lg font-medium">No Active Task</div>
      <div class="mt-2 text-2xl font-mono">Time: {{ timer }}s</div>
    </div>
  </div>
</template>

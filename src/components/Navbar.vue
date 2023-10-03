<template>
  <nav
    class="border-gray-200 shadow-sm bg-gray-50 dark:bg-white dark:border-white"
  >
    <div
      class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
    >
      <a href="#" class="flex items-center">
        <span
          class="self-center text-2xl font-semibold whitespace-nowrap dark:text-black"
          >Where in the world?</span
        >
      </a>
      <a @click="toggleDarkMode" class="flex items-center gap-2 cursor-pointer">
        <svg
          class="w-6 h-6 text-gray-800 dark:text-black"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 18 20"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M8.509 5.75c0-1.493.394-2.96 1.144-4.25h-.081a8.5 8.5 0 1 0 7.356 12.746A8.5 8.5 0 0 1 8.509 5.75Z"
          />
        </svg>
        <span class="self-center whitespace-nowrap dark:text-black"
          >Toggle Dark</span
        >
      </a>
    </div>
  </nav>
</template>
<script setup>
import { ref } from "vue";
const isDarkMode = ref(false);
const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value;
  document.documentElement.classList.toggle("dark-mode", isDarkMode.value);
};
</script>

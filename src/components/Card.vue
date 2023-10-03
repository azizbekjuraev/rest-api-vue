<template>
  <div>
    <main class="flex mt-4 gap-2 justify-center flex-wrap mx-auto">
      <!-- primera card -->
      <div
        v-for="item in filteredData"
        class="bg-white w-72 h-96 shadow-md rounded m-3"
      >
        <div class="h-3/5 w-full">
          <img
            class="w-full h-full object-cover rounded-t"
            :src="item.flag"
            alt="piña"
          />
        </div>
        <div class="w-full h-1/2 p-3">
          <a href="#" class="hover:text-yellow-600 text-gray-700">
            <span class="text-lg font-semibold uppercase tracking-wide">{{
              item.name
            }}</span>
          </a>
          <p class="text-gray-600 text-sm leading-5 mt-1">
            Population: {{ item.population }}
          </p>
          <p class="text-gray-600 text-sm leading-5 mt-1">
            Region: {{ item.region }}
          </p>
          <p class="text-gray-600 text-sm leading-5 mt-1">
            Capital: {{ item.capital }}
          </p>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
defineProps(["filteredData"]);
</script>

<style scoped>
/* Add your component-specific styles here */
</style>

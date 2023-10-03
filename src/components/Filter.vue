<template>
  <div class="md:flex justify-between py-4 md:px-20 mt-4">
    <!-- Left Side: Search Field -->
    <div class="md:w-1/3 px-4 mb-2 md:mb-0">
      <input
        type="text"
        class="w-full bg-white border rounded-md py-2 px-4 focus:outline-none focus:ring focus:border-blue-300"
        placeholder="Search..."
        v-model="searchQuery"
      />
    </div>

    <!-- Right Side: Filter Dropdown -->
    <div class="w-1/2 md:w-1/4 px-4">
      <div class="relative">
        <select
          class="w-full appearance-none bg-white border rounded-md py-2 px-4 pr-8 focus:outline-none focus:ring focus:border-blue-300"
          v-model="selectedFilter"
        >
          <option value="" selected disabled>Filter by Region</option>
          <option v-for="region in allRegions" :key="region" :value="region">
            {{ region }}
          </option>
        </select>
        <div
          class="absolute inset-y-0 right-0 flex items-center pr-3 pointer-events-none"
        >
          <svg
            class="h-5 w-5 text-gray-400"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 20 20"
            fill="currentColor"
            aria-hidden="true"
          >
            <path
              fill-rule="evenodd"
              d="M7.293 6.293a1 1 0 011.414 0L10 7.586l1.293-1.293a1 1 0 111.414 1.414l-2 2a1 1 0 01-1.414 0l-2-2a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </div>
      </div>
    </div>
  </div>
  <Card :filteredData="filteredData" />
</template>

<script setup>
import apiData from "../../data.json";
import Card from "./Card.vue";
import { ref, computed, watch } from "vue";
const searchQuery = ref("");
const selectedFilter = ref("");

const filteredData = computed(() => {
  let filtered = apiData;
  if (selectedFilter.value) {
    filtered = filtered.filter((item) => item.region === selectedFilter.value);
  }
  if (searchQuery.value) {
    const query = searchQuery.value.toLowerCase();
    filtered = filtered.filter((item) => {
      return (
        item?.name?.toLowerCase().includes(query) ||
        item?.capital?.toLowerCase().includes(query)
      );
    });
  }
  return filtered;
});

const allRegions = computed(() => {
  const regionSet = new Set(); // Use a Set to automatically deduplicate
  apiData.forEach((item) => {
    regionSet.add(item.region); // Assuming 'region' is the property containing region names
  });
  return Array.from(regionSet); // Convert Set back to an array
});
</script>

<style scoped></style>

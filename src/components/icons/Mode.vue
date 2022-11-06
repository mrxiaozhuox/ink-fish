<script setup lang="ts">
import { inject, type Ref } from "vue";
const isDarkMode: Ref<boolean> = inject("isDarkTheme")!;
</script>

<template>
  <div :class="[isDarkMode ? 'i-mdi-moon-waxing-crescent text-gray-200' : 'i-mdi-weather-sunny text-orange-500' ]" text-xl />
</template>

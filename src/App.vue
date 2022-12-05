<script setup lang="ts">
import { RouterView } from "vue-router";
import Navbar from "@/components/Navbar.vue";
import { ref, provide } from "vue";

const darkTheme = ref(localStorage.getItem("theme") == "dark");
provide("isDarkTheme", darkTheme);

if (darkTheme.value) {
  document.documentElement.classList.add("dark");
  document.documentElement.classList.add("bg-gray-800");
} else {
  document.documentElement.classList.remove("dark");
  document.documentElement.classList.remove("bg-gray-800");
}
</script>

<template>
  <Navbar />
  <RouterView />
</template>

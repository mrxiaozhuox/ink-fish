<script setup lang="ts">
import { getCurrentInstance, inject, type Ref } from "vue";
import ModeIcon from "./icons/Mode.vue";

let app = getCurrentInstance();

let current: Ref<boolean> = inject("isDarkTheme")!;

function changeState() {
  current.value = !current.value;
  localStorage.setItem("theme", current.value ? "dark" : "light");
  if (current.value) {
    document.documentElement.classList.add("dark");
    document.documentElement.classList.add("bg-gray-800");
  } else {
    document.documentElement.classList.remove("dark");
    document.documentElement.classList.remove("bg-gray-800");
  }
}
</script>
<template>
  <button @click="changeState">
    <ModeIcon />
  </button>
</template>

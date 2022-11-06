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
  } else {
    document.documentElement.classList.remove("dark");
  }
}
</script>
<template>
  <button @click="changeState">
    <ModeIcon />
  </button>
</template>

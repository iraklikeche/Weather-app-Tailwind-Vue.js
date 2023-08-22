<script setup>
import { RouterLink, RouterView } from "vue-router";
import SideNavigation from "./components/SideNavigation.vue";
</script>

<template>
  <div class="flex flex-col min-h-screen font-Roboto bg-weather-primary">
    <SideNavigation />
    <RouterView />
  </div>
</template>

<style scoped></style>

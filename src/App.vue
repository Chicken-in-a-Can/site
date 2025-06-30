<script setup>
  import TitleBar from "@/TitleBar.vue";
  import { RouterView } from "vue-router";
</script>

<template>
  <div class="p-8">
    <TitleBar/>
  </div>
  <RouterView/>
</template>
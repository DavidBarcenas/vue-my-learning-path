<template>
  <app-header></app-header>
</template>

<script>
import { defineAsyncComponent } from "vue";

const AppHeader = defineAsyncComponent(() => import("./components/header.vue"));

export default {
  components: { AppHeader },
};
</script>

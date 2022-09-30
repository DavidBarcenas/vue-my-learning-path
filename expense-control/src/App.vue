<script setup lang="ts">
import SplashScreen from "./components/splash-screen.vue";
import Home from "./components/home.vue";
</script>

<script lang="ts">
export default {
  name: "app-root",
};
</script>

<template>
  <Suspense>
    <Home />
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

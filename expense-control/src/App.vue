<script setup lang="ts">
import SplashScreen from "./components/splash-screen.vue";
import Home from "./components/home.vue";
</script>

<template>
  <Suspense>
    <Home />
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>

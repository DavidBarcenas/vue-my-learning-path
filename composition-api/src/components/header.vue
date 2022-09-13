<template>
  <header>
    <h1>Composition API</h1>
    <button @click="show = !show">Menu</button>
    <transition name="fade">
      <app-menu v-show="show"></app-menu>
    </transition>
  </header>
</template>

<script>
import AppMenu from "./menu.vue";

export default {
  name: "app-header",
  components: { AppMenu },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<style>
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
</style>

<template>
  <header>
    <h1>Composition API - {{ name }}</h1>
    <button @click="show = !show">Menu</button>
    <transition name="fade">
      <app-menu v-show="show"></app-menu>
    </transition>
  </header>
</template>

<script>
import { ref, toRef } from "vue";
import AppMenu from "./menu.vue";

export default {
  name: "app-header",
  components: { AppMenu },
  props: {
    fullName: String,
  },
  setup(props) {
    const show = ref(false);
    const name = toRef(props, "fullName");

    return {
      show,
      name,
    };
  },
};
</script>

<style scoped>
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
</style>

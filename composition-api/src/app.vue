<template>
  <app-header></app-header>
  <button @click="toggleModal">Toggle modal</button>
  <modal :showModal="show" text="Are you sure?" />
  <h2>{{ counter }}</h2>
</template>

<script>
import { defineAsyncComponent, onMounted, onUnmounted, ref } from "vue";
import Modal from "./components/modal.vue";

const AppHeader = defineAsyncComponent(() => import("./components/header.vue"));

export default {
  components: { AppHeader, Modal },
  setup(props, context) {
    const show = ref(false);
    const counter = ref(0);

    onMounted(() => console.log("mounted", context));
    onUnmounted(() => console.log("onUnmounted"));

    setInterval(() => counter.value++, 1000);

    return {
      show,
      counter,
    };
  },
  methods: {
    toggleModal() {
      this.show = !this.show;
    },
  },
};
</script>

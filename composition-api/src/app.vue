<template>
  <app-header></app-header>
  <button @click="toggleModal">Toggle modal</button>
  <modal :showModal="show" text="Are you sure?" />
</template>

<script>
import { defineAsyncComponent } from "vue";
import Modal from "./components/modal.vue";

const AppHeader = defineAsyncComponent(() => import("./components/header.vue"));

export default {
  components: { AppHeader, Modal },
  data() {
    return {
      show: false,
    };
  },
  methods: {
    toggleModal() {
      this.show = !this.show;
    },
  },
};
</script>

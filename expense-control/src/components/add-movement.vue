<script setup lang="ts">
import { ref } from "vue";
import Modal from "./modal.vue";

const showModal = ref(false);
</script>

<script lang="ts">
export default {
  name: "app-add-movement",
};
</script>

<template>
  <button @click="showModal = true">Add movement</button>
  <teleport to="#app">
    <Modal v-show="showModal" @close="showModal = false"> Add Form </Modal>
  </teleport>
</template>

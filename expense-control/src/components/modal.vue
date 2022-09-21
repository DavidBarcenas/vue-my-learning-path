<script setup lang="ts">
const emit = defineEmits(["close"]);
function closeModal() {
  emit("close");
}
</script>
<script lang="ts">
export default {
  name: "app-modal",
};
</script>

<template>
  <div class="modal">
    <div class="header">
      <p>New movement</p>
      <span @click="closeModal">X</span>
    </div>
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background: #fff;
  color: var(--vt-c-black);
  padding: 2rem;
  z-index: 2;
}
.modal .header {
  display: flex;
  justify-content: space-between;
  font-weight: bold;
  font-size: 1.25rem;
}
</style>

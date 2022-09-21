<script setup lang="ts">
function reload() {
  location.reload();
}
</script>

<script lang="ts">
export default {
  name: "app-header",
};
</script>

<template>
  <header class="header">
    <img src="../assets/logo.svg" alt="Vue Logo" width="40" @click="reload" />
    <h1>Expense</h1>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 1rem;
}

.header h1 {
  margin-left: 1rem;
}
</style>

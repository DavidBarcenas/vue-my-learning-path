<script setup lang="ts">
import Layout from "./layout.vue";
import Header from "./header.vue";
</script>

<script lang="ts">
export default {
  name: "app-home",
};
</script>

<template>
  <Layout>
    <template #header>
      <Header></Header>
    </template>
  </Layout>
</template>

<script setup lang="ts">
import Layout from "./layout.vue";
import Header from "./header.vue";
import Resume from "./resume.vue";
import Movements from "./movements.vue";
</script>

<script lang="ts">
export default {
  name: "app-home",
};
</script>

<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume />
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

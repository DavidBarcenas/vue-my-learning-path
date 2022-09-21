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
      <Resume :label="'Ahorro total'" :amount="5000" :total-amount="54321">
        <template #chart>
          <h3>Chart</h3>
        </template>
        <template #actions>
          <button>Calculate</button>
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements />
    </template>
  </Layout>
</template>

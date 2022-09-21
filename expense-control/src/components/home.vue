<script setup lang="ts">
import Layout from "./layout.vue";
import Header from "./header.vue";
import Resume from "./resume.vue";
import Movements from "./movements.vue";

const moveList = [
  {
    id: 0,
    title: "Movement 1",
    description: "lorem ipsum",
    amount: 234,
  },
  {
    id: 1,
    title: "Movement 2",
    description: "lorem ipsum",
    amount: 2323,
  },
  {
    id: 2,
    title: "Movement 3",
    description: "lorem ipsum",
    amount: 43534,
  },
  {
    id: 3,
    title: "Movement 4",
    description: "lorem ipsum",
    amount: 43534,
  },
  {
    id: 4,
    title: "Movement 5",
    description: "lorem ipsum",
    amount: 43534,
  },
  {
    id: 5,
    title: "Movement 6",
    description: "lorem ipsum",
    amount: 43534,
  },
  {
    id: 6,
    title: "Movement 7",
    description: "lorem ipsum",
    amount: 43534,
  },
];
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
      <Movements :list="moveList" />
    </template>
  </Layout>
</template>

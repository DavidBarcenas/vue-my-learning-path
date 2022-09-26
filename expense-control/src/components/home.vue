<script setup lang="ts">
import Layout from "./layout.vue";
import Header from "./header.vue";
import Resume from "./resume.vue";
import Movements from "./movements.vue";
import AddMovement from "./add-movement.vue";
import Graphic from "./graphic.vue";
import { computed } from "vue";

let moveList = [
  {
    id: 0,
    title: "Movement 1",
    description: "lorem ipsum",
    amount: 234,
    time: new Date("09-01-2022"),
  },
  {
    id: 1,
    title: "Movement 2",
    description: "lorem ipsum",
    amount: 2323,
    time: new Date("09-01-2022"),
  },
  {
    id: 2,
    title: "Movement 3",
    description: "lorem ipsum",
    amount: 43534,
    time: new Date("09-01-2022"),
  },
  {
    id: 3,
    title: "Movement 4",
    description: "lorem ipsum",
    amount: 43534,
    time: new Date("09-01-2022"),
  },
  {
    id: 4,
    title: "Movement 5",
    description: "lorem ipsum",
    amount: 43534,
    time: new Date("09-01-2022"),
  },
  {
    id: 5,
    title: "Movement 6",
    description: "lorem ipsum",
    amount: 43534,
    time: new Date("09-01-2022"),
  },
  {
    id: 6,
    title: "Movement 7",
    description: "lorem ipsum",
    amount: 43534,
    time: new Date("09-01-2022"),
  },
];

const graphicAmounts = computed(() => {
  const lastDays = moveList
    .filter((m) => {
      const today = new Date();
      const oldDate = today.setDate(today.getDate() - 30);
      return m.time > oldDate;
    })
    .map((m) => m.amount);

  return lastDays.map((m, i) => {
    const lastMovements = lastDays.slice(0, i);
    return lastMovements.reduce((sum, movement) => {
      return sum + movement;
    }, 0);
  });
});

const handleRemove = (id: number) => {
  moveList = moveList.filter((movement) => movement.id != id);
};
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
          <Graphic :amounts="graphicAmounts" />
        </template>
        <template #actions>
          <AddMovement />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :list="moveList" @remove="handleRemove" />
    </template>
  </Layout>
</template>

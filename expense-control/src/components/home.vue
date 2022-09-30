<script setup lang="ts">
import Layout from "./layout.vue";
import Header from "./header.vue";
import Resume from "./resume.vue";
import Movements from "./movements.vue";
import AddMovement from "./add-movement.vue";
import Graphic from "./graphic.vue";
import { computed, onMounted, ref, type Ref } from "vue";

let moveList: Ref<any[]> = ref([]);

const graphicAmounts = computed(() => {
  const lastDays = moveList.value
    .filter((m) => {
      const today = new Date();
      const oldDate = today.setDate(today.getDate() - 30);
      return new Date().setDate(m.time.getDate()) > oldDate;
    })
    .map((m) => m.amount);

  return lastDays.map((m, i) => {
    const lastMovements = lastDays.slice(0, i + 1);
    return lastMovements.reduce((sum, movement) => {
      return sum + movement;
    }, 0);
  });
});

const handleRemove = (id: number) => {
  moveList.value = moveList.value.filter((movement) => movement.id != id);
  save();
};

function create(movement: any) {
  moveList.value.push(movement);
  save();
}

function save() {
  localStorage.setItem("movements", JSON.stringify(moveList.value));
}

onMounted(() => {
  const movements = localStorage.getItem("movements");
  if (movements) {
    moveList.value = JSON.parse(movements);
  }
});
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
          <AddMovement @create="create" />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :list="moveList" @remove="handleRemove" />
    </template>
  </Layout>
</template>

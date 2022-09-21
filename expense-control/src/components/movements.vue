<script setup lang="ts">
import { computed } from "vue";

defineProps<{
  list: Array<any>;
}>();

const emit = defineEmits(["remove"]);
const remove = (id: number) => emit("remove", id);
const isNegative = (amount: number) => computed(() => amount < 0);
</script>

<script lang="ts">
export default {
  name: "app-movements",
};
</script>

<template>
  <div>
    <h2>Historial</h2>
    <div class="content">
      <div v-for="item in list" :key="item.id">
        <h3>{{ item.title }}</h3>
        <p>{{ item.description }}</p>
        <span
          :class="{
            red: isNegative(item.amount).value,
            green: !isNegative(item.amount).value,
          }"
          >{{ item.amount }}</span
        >
        <button @click="remove(item.id)">delete</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.red {
  color: red;
}
.green {
  color: green;
}
</style>

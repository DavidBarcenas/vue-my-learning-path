<script setup lang="ts">
import { computed } from "vue";

const { label, amount, totalAmount } = defineProps<{
  label: string;
  amount: number;
  totalAmount: number;
}>();

const total = computed(() => (amount ? amount : totalAmount));
</script>

<script lang="ts">
export default {
  name: "app-resume",
};
</script>

<template>
  <div class="resume-container">
    <p>{{ label }}</p>
    <h2>{{ total }}</h2>
  </div>
</template>

<style scoped>
.resume-container {
  text-align: center;
  margin-top: 3rem;
}
.resume-container p {
  font-size: 1.5rem;
  margin-bottom: 0;
}
.resume-container h2 {
  font-size: 3rem;
  color: #6fdd6f;
  font-weight: bold;
  line-height: normal;
}
</style>

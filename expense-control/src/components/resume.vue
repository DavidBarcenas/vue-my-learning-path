<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{
  label: string;
  amount: number;
  totalAmount: number;
}>();
const total = computed(() => (props.amount ? props.amount : props.totalAmount));
const amountCurrency = computed(() => currencyFormatter.format(total.value));
const currencyFormatter = new Intl.NumberFormat("es-MX", {
  style: "currency",
  currency: "MXN",
});
</script>

<script lang="ts">
export default {
  name: "app-resume",
};
</script>

<template>
  <div class="resume-container">
    <p>{{ label }}</p>
    <h2>{{ amountCurrency }}</h2>
    <div class="chart">
      <slot name="chart"></slot>
    </div>
    <div class="actions">
      <slot name="actions"></slot>
    </div>
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
.resume-container .chart {
  width: 50%;
  margin: auto;
}
</style>

<script setup lang="ts">
import { computed, toRefs } from "vue";

const props = defineProps<{
  amounts: Array<number>;
}>();

const { amounts } = toRefs(props);

const points = computed(() => {
  const totalItems = amounts.value.length;
  return Array(totalItems)
    .fill(100)
    .reduce((points, amount, i) => {
      const x = (300 / totalItems) * (i + 1);
      const y = convertToPixels(amount);
      return `${points} ${x}, ${y}`;
    }, "0, 100");
});

function convertToPixels(amount: number) {
  const min = Math.min(amount);
  const max = Math.max(amount);

  return `${min}, ${max}`;
}
</script>

<script lang="ts">
export default {
  name: "app-graphic",
};
</script>

<template>
  <div>
    <svg viewBox="0 0 300 200">
      <line stroke="#fff" stroke-width="2" x1="0" y1="100" x2="300" y2="100" />
      <polyline
        fill="none"
        stroke="#6fdd6f"
        stroke-width="2"
        :points="points"
      />
      <line
        stroke="#ebebeba3"
        stroke-width="2"
        x1="200"
        y1="0"
        x2="200"
        y2="200"
      />
    </svg>
  </div>
</template>

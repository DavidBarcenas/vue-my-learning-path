<script setup lang="ts">
import { computed, ref, toRefs } from "vue";

const props = defineProps<{
  amounts: Array<number>;
}>();
const { amounts } = toRefs(props);
const showPointer = ref(false);
const pointer = ref(0);

const zero = computed(() => convertToPixels(0));

const points = computed(() => {
  const totalItems = amounts.value.length;
  return amounts.value.reduce((points, amount, i) => {
    const x = (300 / totalItems) * (i + 1);
    const y = convertToPixels(amount);
    return `${points} ${x},${y}`;
  }, "0, 100");
});

function convertToPixels(amount: number) {
  const min = Math.min(...amounts.value);
  const max = Math.max(...amounts.value);
  const amountAbsolute = amount + Math.abs(min);
  const minmax = Math.abs(max) + Math.abs(min);

  return 200 - ((amountAbsolute * 100) / minmax) * 2;
}

function tap({ target, touches }: any) {
  showPointer.value = true;

  const elWidth = target.getBoundingClientRect().width;
  const elementX = target.getBoundingClientRect().x;
  const touchX = touches[0].clientX;

  pointer.value = ((touchX - elementX) * 300) / elWidth;
}

function untap() {
  showPointer.value = false;
}
</script>

<script lang="ts">
export default {
  name: "app-graphic",
};
</script>

<template>
  <div>
    <svg
      @touchstart="tap"
      @touchmove="tap"
      @touchend="untap"
      viewBox="0 0 300 200"
    >
      <line
        stroke="#fff"
        stroke-width="2"
        x1="0"
        :y1="zero"
        x2="300"
        :y2="zero"
      />
      <polyline
        fill="none"
        stroke="#6fdd6f"
        stroke-width="2"
        :points="points"
      />
      <line
        v-show="showPointer"
        stroke="#4FC3F7"
        stroke-width="2"
        :x1="pointer"
        y1="0"
        :x2="pointer"
        y2="200"
      />
    </svg>
  </div>
</template>

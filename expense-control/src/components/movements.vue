<script setup lang="ts">
defineProps<{
  list: Array<any>;
}>();
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
        <span>{{ item.amount }}</span>
      </div>
    </div>
  </div>
</template>

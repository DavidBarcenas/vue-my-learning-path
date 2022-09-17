<template>
  <nav ref="menu">
    <ul>
      <li>Home</li>
      <li>About</li>
      <li>Contact</li>
      <li>{{ username }}</li>
    </ul>
  </nav>
</template>

<script>
import { inject, onMounted, ref } from "vue";

export default {
  name: "app-menu",
  setup() {
    const username = inject("username");
    const menu = ref(null);

    onMounted(() => {
      console.log(menu.value);
    });

    return {
      username,
      menu,
    };
  },
};
</script>

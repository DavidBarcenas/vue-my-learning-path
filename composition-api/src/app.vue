<template>
  <component :is="dynamic"></component>
</template>

<script>
import AppHeader from "./components/header.vue";

export default {
  components: {
    AppHeader,
  },
  data() {
    return {
      dynamic: "AppHeader",
    };
  },
};
</script>

<template>
  <app-header :fullName="fullName"></app-header>
  <button @click="toggleModal">Toggle modal</button>
  <modal :showModal="show" text="Are you sure?" />
  <h2>{{ counter }} - {{ fullName }}</h2>
</template>

<script>
import {
  defineAsyncComponent,
  onMounted,
  onUnmounted,
  ref,
  watch,
  computed,
  provide,
} from "vue";
import Modal from "./components/modal.vue";

const AppHeader = defineAsyncComponent(() => import("./components/header.vue"));

export default {
  components: { AppHeader, Modal },
  setup(props, context) {
    const show = ref(false);
    const counter = ref(0);
    const firstName = ref("David");
    const lastName = ref("Barcenas");

    onMounted(() => console.log("mounted", context));
    onUnmounted(() => console.log("onUnmounted"));

    // setInterval(() => counter.value++, 1000);

    watch(counter, (curr, prev) => {
      console.log(curr, prev);
    });

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    provide("username", "Davepro");

    return {
      show,
      counter,
      fullName,
    };
  },
};
</script>

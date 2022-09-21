<script lang="ts">
export default {
  name: "app-layout",
  data() {
    return {
      showMovements: false,
    };
  },
};
</script>

<template>
  <slot name="header"></slot>
  <div class="resume">
    <slot name="resume"></slot>
  </div>
  <div class="movements">
    <div class="header" @click="showMovements = !showMovements">
      <div class="grip"></div>
    </div>
    <div class="body" v-show="showMovements">
      <slot name="movements"></slot>
    </div>
  </div>
</template>

<style scoped>
.resume {
  min-height: 80vh;
}
.movements {
  position: fixed;
  left: 0;
  bottom: 1rem;
  width: 100%;
  z-index: 10;
  max-height: 70%;
  background-color: #fff;
  color: #717171;
  text-align: center;
  overflow-y: scroll;
}
.movements .header {
  height: 4rem;
  padding-top: 1.5rem;
}
.movements .grip {
  display: block;
  width: 100px;
  height: 10px;
  background-color: #717171;
  border-radius: 10px;
  margin: 0 auto;
}
.movements .body {
  width: 100%;
  height: 70vh;
}
</style>

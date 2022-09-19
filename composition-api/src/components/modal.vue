<template>
  <teleport to="body">
    <div class="modal" v-if="showModal">
      <h1>Delete item</h1>
      <p>{{ text }}</p>
      <button>Cancel</button>
      <button>Ok</button>
    </div>
  </teleport>
</template>
<script>
export default {
  props: ["showModal", "text"],
};
</script>

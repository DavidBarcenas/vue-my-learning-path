<script setup lang="ts">
import { ref } from "vue";
import Modal from "./modal.vue";

const showModal = ref(false);
const title = ref("");
const amount = ref(0);
const description = ref("");
const type = ref("Entry");
const emit = defineEmits(["create"]);

function handleSubmit(e: any) {
  showModal.value = !showModal.value;
  emit("create", {
    title: title.value,
    description: description.value,
    amount: type.value === "Entry" ? amount.value : -amount.value,
    time: new Date(),
    id: new Date(),
  });
}
</script>

<script lang="ts">
export default {
  name: "app-add-movement",
};
</script>

<template>
  <button @click="showModal = true">Add movement</button>
  <teleport to="#app">
    <Modal v-show="showModal" @close="showModal = false">
      <form @submit.prevent="handleSubmit">
        <div class="field">
          <label for="title">Title</label>
          <input type="text" id="title" v-model="title" />
        </div>
        <div class="field">
          <label for="amount">Amount</label>
          <input type="number" id="amount" v-model="amount" />
        </div>
        <div class="field">
          <label for="description">Description</label>
          <textarea
            id="description"
            cols="30"
            rows="5"
            v-model="description"
          ></textarea>
        </div>
        <div class="field">
          <label>Type</label>
          <input type="radio" v-model="type" value="Entry" />
          <input type="radio" v-model="type" value="Expense" />
        </div>
        <button>Submit</button>
      </form>
    </Modal>
  </teleport>
</template>

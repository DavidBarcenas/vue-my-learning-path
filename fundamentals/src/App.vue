<script>
export default {
  data() {
    return {
      counter: 0,
      attr: "src",
      imageUrl:
        "https://images.pexels.com/photos/8581056/pexels-photo-8581056.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    };
  },
  methods: {
    incrementCount() {
      this.counter++;
    },
    onSubmit() {
      console.log("Sending form");
    },
  },
};
</script>

<template>
  <img v-bind:[attr]="imageUrl" alt="Random image" width="200" />
  <h1>count is {{ counter }}</h1>
  <button v-on:click="incrementCount">increment</button>

  <form v-on:submit.prevent="onSubmit">
    <input type="text" name="fullName" />
    <button>Send</button>
  </form>
</template>

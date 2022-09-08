<script>
export default {
  data() {
    return {
      text: "Use attributes and events",
      textWithModel: "Use v-model",
      firstName: "Dave",
      lastName: "Bárcenas",
      currentDate: new Date(),
    };
  },
  methods: {
    input(e) {
      this.text = e.target.value;
    },
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    formatDate() {
      return this.currentDate.toLocaleDateString("es-mx");
    },
  },
};
</script>

<template>
  <h1>{{ text }} - {{ textWithModel }}</h1>
  <input type="text" @input="input" :value="text" />
  <input type="text" v-model="firstName" />

  <h2>{{ fullName }}</h2>
  <p>{{ formatDate }}</p>
</template>

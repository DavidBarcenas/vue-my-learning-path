<script>
export default {
  data() {
    return {
      text: "Use attributes and events",
      textWithModel: "Use v-model",
      firstName: "Dave",
      lastName: "Bárcenas",
      currentDate: new Date(),
      posts: [{ message: "foo" }, { message: "bar" }],
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
  watch: {
    text(value) {
      console.log("Watcher activated! ", value);
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

  <div class="list">
    <div class="item" v-for="(item, index) in posts" :key="index">
      <h4>Title - {{ index }}</h4>
      <p>lorem ipsum</p>
    </div>
  </div>
</template>

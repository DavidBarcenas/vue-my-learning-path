<script>
export default {
  data() {
    return {
      attr: "src",
      imageUrl:
        "https://images.pexels.com/photos/8581056/pexels-photo-8581056.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    };
  },
};
</script>

<template>
  <img v-bind:[attr]="imageUrl" alt="Random image" />
  <button>Get random image</button>
</template>

<template>
  <img :src="image" class="image" alt="Main image" />
</template>

<script>
export default {
  name: "MainImage",
  props: {
    image: {
      type: String,
      default: () => "sss",
    },
  },
};
</script>

<style scoped>
.image {
  width: 100%;
  max-width: 500px;
}
</style>
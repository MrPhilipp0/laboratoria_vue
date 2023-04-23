<template>
  <img :src="image" class="image" alt="Mini image" />
</template>

<script>
export default {
  name: "MiniImage",
  props: {
    image: {
      type: String,
      default: () => "",
    },
  },
};
</script>

<style scoped>
.image {
  width: 100%;
  max-width: 100px;
}
</style>
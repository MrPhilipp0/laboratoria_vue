<template>
  <div class="wrapper" v-if="image">
    <div class="modal">
      <button class="close-modal" @click="closeModal">X</button>
      <img :src="image" class="image" alt="Main image" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    image: {
      type: String,
      default: () => "",
    },
  },
  methods: {
    closeModal() {
      this.$emit("closeModal");
      this.image = "";
    },
  },

  created() {
    this.$nuxt.$on("showModal", (href) => (this.image = href));
  },
};
</script>

<style scoped>
.wrapper {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  z-index: 10;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 450px;
  height: 500px;
  background-color: rgb(246, 246, 246);
  border-radius: 4px;
}

.close-modal {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 4px 8px;
  cursor: pointer;
  font-weight: 600;
  font-size: 14px;
  border: 1px solid rgb(9, 107, 79);
  background-color: rgba(5, 120, 87, 1);
  color: white;
  border-radius: 4px;
}

.image {
  width: auto;
  max-height: 350px;
  max-width: 425px;
}
</style>
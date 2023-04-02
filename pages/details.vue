<template>
  <div>
    <TopNav />
    <Modal
      image="https://static.nike.com/a/images/t_PDP_864_v1/f_auto,b_rgb:f5f5f5/3f3e7049-5c99-428c-abcd-e246b086f2ed/buty-meskie-air-force-1-07-VJhk3P.png"
      v-if="dupa"
      @closeModal="showModal"
    />
    <button
      @click="showInfo"
      class="show-button"
    >
      Show image
    </button>
    <div
      class="show-modal"
      @click="showModal"
    >
      <MainImage
        class="main-image"
        image="https://static.nike.com/a/images/t_PDP_864_v1/f_auto,b_rgb:f5f5f5/3f3e7049-5c99-428c-abcd-e246b086f2ed/buty-meskie-air-force-1-07-VJhk3P.png"
      />
    </div>
  </div>
</template>

<script>
import TopNav from "../components/nav/TopNav.vue";
import MainImage from "../components/gallery/main-img.vue";
import Modal from "../components/gallery/modal.vue";

export default {
  name: "DetailsPage",
  components: { TopNav, MainImage, Modal },
  methods: {
    showInfo: () => {
      alert("Hello my friend!");
    },

    showModal() {
      this.dupa = !this.dupa;
    }
  },

  data() {
    return {
      dupa: false,
    }
  },
};
</script>

<style scoped>
.show-button {
  cursor: pointer;
  margin: 16px;
  font-weight: 600;
  padding: 8px 16px;
  font-size: 14px;
  border: 1px solid rgb(9, 107, 79);
  background-color: rgba(5, 120, 87, 1);
  color: white;
  border-radius: 4px;
}

.main-image {
  display: block;
  margin: 16px auto;
}

.show-modal {
  cursor: pointer;
}
</style>
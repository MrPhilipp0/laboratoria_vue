<template>
  <div>
    <Modal
      :image="viewedImage.src"
      v-if="modalIsActive"
      @closeModal="showModal"
    />
    <div>
      <button @click="previousMainImage">left</button>
      <div class="show-modal" @click="showModal">
        <MainImage class="main-image" :image="viewedImage.src" />
      </div>
      <button @click="nextMainImage">rigth</button>
    </div>
    <div class="mini-image-wrapper">
      <div
        v-for="imageSrc in IMAGES_SRCS"
        :key="imageSrc"
        @click="setMainImage(imageSrc)"
      >
        <MiniImage
          :image="imageSrc.src"
          class="mini-image"
          :class="{ 'mini-image--active': imageSrc.id === viewedImage.id }"
        />
      </div>
    </div>
  </div>
</template>

<script>
import MainImage from "../../components/gallery/main-img.vue";
import MiniImage from "../../components/gallery/mini-img.vue";
import Modal from "../../components/gallery/modal.vue";
import { ImagesSrcs } from "../../constants/images.const";

export default {
  name: "DetailsPage",
  components: { MainImage, Modal, MiniImage },
  methods: {
    showModal() {
      this.modalIsActive = !this.modalIsActive;
    },

    setMainImage(image) {
      this.viewedImage = image;
    },

    nextMainImage() {
      const nextImageId = (this.viewedImage.id + 1) % ImagesSrcs.length;
      this.viewedImage = this.IMAGES_SRCS.find(
        (image) => image.id === nextImageId
      );
    },

    previousMainImage() {
      const previousImageId =
        this.viewedImage.id - 1 < 0
          ? ImagesSrcs.length - 1
          : this.viewedImage.id - 1;

      this.viewedImage = this.IMAGES_SRCS.find(
        (image) => image.id === previousImageId
      );
    },
  },

  data() {
    return {
      modalIsActive: false,
      viewedImage: ImagesSrcs[0],
    };
  },

  created() {
    this.IMAGES_SRCS = ImagesSrcs;
  },
};
</script>

<style scoped>
.main-image {
  display: block;
  margin: 16px auto;
}

.show-modal {
  cursor: pointer;
}

.mini-image {
  box-shadow: 0px 0px 24px -5px rgba(66, 68, 90, 1);
  transition: 0.2s;
}

.mini-image--active {
  box-shadow: 0px 0px 24px -5px rgb(58, 73, 236);
}

.mini-image:hover {
  scale: 1.1;
  cursor: pointer;
}

.mini-image-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
}
</style>


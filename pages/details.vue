<template>
  <div>
    <TopNav />
    <button class="show-button" @click="showInfo">Show image</button>
    <MainImage
      class="main-image"
      image="https://static.nike.com/a/images/t_PDP_864_v1/f_auto,b_rgb:f5f5f5/3f3e7049-5c99-428c-abcd-e246b086f2ed/buty-meskie-air-force-1-07-VJhk3P.png"
    />
  </div>
</template>

<script>
import TopNav from "../components/nav/TopNav.vue";
import MainImage from "../components/gallery/main-img.vue";
export default {
  name: "DetailsPage",
  components: { TopNav, MainImage },

  methods: {
    showInfo: () => {
      alert("Hello my friend!");
    },
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
</style>
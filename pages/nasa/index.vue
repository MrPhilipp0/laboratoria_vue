<template>
  <div>
    <div class="search">
      <input v-model="search" placeholder="Search content..." />
      <button @click="($event) => searchData()">Search</button>
    </div>

    <div class="wrapper">
      <div
        v-for="(value, index) in dataArray"
        :key="index"
        class="image"
        @click="showModal(value)"
      >
        <MiniImage :image="value" class="mini-image" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import MiniImage from "../../components/gallery/mini-img.vue";

export default {
  name: "index",
  components: { MiniImage },

  created() {
    this.fetchData();
  },

  data() {
    return {
      dataArray: [],
      search: "sun",
    };
  },

  methods: {
    showModal(href = "") {
      this.$nuxt.$emit("showModal", href);
    },

    searchData() {
      this.fetchData(this.search);
    },

    async fetchData(search = "sun") {
      const options = {
        method: "GET",
        url: `https://images-api.nasa.gov/search?q=${search}`,
      };

      await axios
        .request(options)
        .then((res) => {
          this.dataArray = res.data.collection.items
            .map(({ links }) => links)
            .filter((links) => Array.isArray(links))
            .map((links) => links[0].href)
            .filter((link) => !!link);
        })
        .catch((error) => alert(error));
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
}

.mini-image {
  box-shadow: 0px 0px 24px -5px rgba(66, 68, 90, 1);
  height: 100%;
  max-height: 100px;
}

.mini-image:hover {
  scale: 1.1;
  cursor: pointer;
}

.search {
  display: flex;
  justify-content: center;
  gap: 4px;
  margin: 8px auto;
}
</style>
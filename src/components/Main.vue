<template>
  <section class="container-fluid">
    <div class="row row-cols-1 row-cols-md-5 g-4 m-5">
      <Album
        v-for="(element, index) in newSearch"
        :key="index"
        :albumObject="element"
      />
    </div>
  </section>
</template>

<script>
import axios from "axios";
import Album from "./Album.vue";

export default {
  name: "IndexMain",
  props: [searchString],
  components: {
    Album,
  },
  data: function () {
    return {
      albumList: undefined,
    };
  },
  created: function () {
    this.getApi();
  },
  methods: {
    getApi() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((result) => {
          this.albumList = result.data.response;
          console.table(this.albumList);
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
  computed: {
    newSearch() {
      return this.albumList.filter((element) =>
        element.response.genre
          .toLowerCase()
          .startWith(this.stringSearch.toLowerCase())
      );
    },
  },
};
</script>

<style lang="scss" scoped>
section {
  margin: 0 auto;
  width: 80%;
  overflow: hidden;
}
</style>
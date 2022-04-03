<template>
  <section class="container-fluid">
    <!-- per vedere se si collega tra header e main -->
    <!-- <div>{{ selectedGenre }}</div> -->
    <div
      class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-5 g-4 m-5"
    >
      <Album
        v-for="(discElement, index) in filterList"
        :key="index"
        :albumList="discElement"
      />
    </div>
  </section>
</template>

//$ :albumList lo invia ad ogni component figlio del main

<script>
import axios from "axios";
import Album from "./Album.vue";

export default {
  name: "MainDiscContainer",
  components: {
    Album,
  },
  //! quello che arriva dall'app
  props: ["selectedGenre"],
  data: function () {
    return {
      genresList: [],
      albumList: [],
    };
  },
  computed: {
    filterList() {
      //se la lista è vuota mi ritorni tutta la lista
      if (this.selectedGenre === "") {
        return this.albumList;
      }
      //se no mi filtri la lista con i vari generi
      return this.albumList.filter(
        (element) => element.genre == this.selectedGenre
      );
    },
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        // mi serve un modo per salvarmi i dischi da qualche parte
        // $ ovvero in un data

        this.albumList = result.data.response;

        // Per ogni album presente nella risposta alla chiamata axios

        this.albumList.forEach((albumElement) => {
          // se non è già presente il genere nella lista dei generi
          // allora aggiungilo
          if (!this.genresList.includes(albumElement.genre)) {
            this.genresList.push(albumElement.genre);
          }
        });
        this.$emit("loadGenres", this.genresList);
      })
      .catch((error) => {
        console.error(error);
      });
  },
};
</script>

<style lang="scss" scoped>
section {
  margin: 0 auto;
  width: 90%;
  overflow: hidden;
}
</style>
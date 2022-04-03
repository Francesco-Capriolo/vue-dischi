<template>
  <div id="app">
    <Header :genresList="genresList" @changedGenre="upSelectedGenres" />
    <Main @loadGenres="upGenresList" :selectedGenre="selectedGenre" />
  </div>
</template>
//£ @changeGenre è l'emit che arriva dall'header all'app e si da una funzione 
// ! :genresList è il props che si invia da app a header
//£ @loadGenres è l'emit che arriva dall'header all'app e si da una funzione
//! :selectedGenre è il props che si invia da app a main
<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data: function () {
    return {
      genresList: [],
      selectedGenre: "",
    };
  },
  methods: {
    // £ la funzione per assegnare ad un data la lista che serve
    upGenresList(genresList) {
      this.genresList = genresList;
    },
    upSelectedGenres(selectedGenre) {
      this.selectedGenre = selectedGenre;
    },
  },
};
</script>

<style lang="scss">
@import "@/style/main-style.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

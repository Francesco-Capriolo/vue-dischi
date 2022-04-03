<template>
  <header class="d-flex justify-content-between align-items-center">
    <nav class="navbar navbar-light">
      <div class="container-fluid">
        <img class="" src="../assets/logo.png" alt="Spoty-logo" />
      </div>
    </nav>
    <div class="me-3">
      <!-- @change per cambiare ogni volta l'emit che si vuole inviare all'app -->
      <select
        class="form-select form-select-sm"
        v-model="selectedGenre"
        @change="$emit('changedGenre', selectedGenre)"
      >
        <option value="">All</option>
        <option
          v-for="(genre, index) in genresList"
          :key="index"
          :value="genre"
        >
          {{ genre }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "IndexHeader",
  props: {
    genresList: Array,
  },
  data: function () {
    return {
      selectedGenre: "",
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
header {
  background-color: #2e3a46;
}
img {
  width: 50px;
}
</style>

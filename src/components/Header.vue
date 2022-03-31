<template>
  <header class="d-flex justify-content-between align-items-center">
    <nav class="navbar navbar-light">
      <div class="container-fluid">
        <img class="" src="../assets/logo.png" alt="Spoty-logo" />
      </div>
    </nav>
    <div class="input-group mb-3 me-2">
      <span class="input-group-text" id="basic-addon3">Choose the Genre</span>
      <input
        type="text"
        class="form-control"
        v-model="inputGenre"
        @keyup="$emit('search', inputGenre)"
      />
    </div>
  </header>
</template>

<script>
export default {
  name: "IndexHeader",
  data: function () {
    return {
      inputGenre: "",
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
div.input-group {
  width: 20%;
}
</style>

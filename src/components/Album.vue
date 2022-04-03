<template>
  <div class="col">
    <div class="card h-100 p-2">
      <img
        :src="albumList.poster"
        class="card-img-top p-2"
        :alt="albumList.title"
      />
      <div class="card-body">
        <h5 class="card-title text-white">{{ albumList.title }}</h5>
        <p class="card-text text-secondary">
          {{ albumList.author }}
        </p>
        <p class="card-text text-secondary">
          {{ albumList.year }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DiscCard",
  // ! il props che viene ricevuto dal main
  props: ["albumList"],
};
</script>

<style lang="scss" scoped>
.card {
  background-color: #2e3a46;
  img {
    height: 160px;
  }
}
</style>
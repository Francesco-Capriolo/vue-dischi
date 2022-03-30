<template>
  <div class="col">
    <div class="card h-100 p-2">
      <img :src="albumObject.poster" class="card-img-top p-2" alt="Album" />
      <div class="card-body">
        <h5 class="card-title text-white">{{ albumObject.title }}</h5>
        <p class="card-text text-secondary">
          {{ albumObject.author }}
        </p>
        <p class="card-text text-secondary">
          {{ albumObject.year }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexAlbum",
  props: { albumObject: Object },
};
</script>

<style lang="scss" scoped>
.card {
  background-color: #2e3a46;
}
</style>
<script>
export default {
  props: {
    filmData: Object,
  },
};
</script>

<template>
  <div class="card">
    <img
      :src="`https://image.tmdb.org/t/p/w342` + filmData.poster_path"
      :alt="filmData.title"
    />
    <p>{{ filmData.title }}</p>
    <p>{{ filmData.original_title }}</p>
    <p>{{ filmData.original_language }}</p>
    <p>{{ filmData.vote_average }}</p>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 100%;
  width: 300px;
  background-color: rgb(58, 58, 58);
  margin-bottom: 2em;

  img {
    width: 200px;
  }
}
</style>

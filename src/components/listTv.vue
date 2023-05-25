<script>
export default {
  props: {
    tvData: Object,
  },
};
</script>

<template>
  <div class="card">
    <img
      :src="`https://image.tmdb.org/t/p/w342` + tvData.poster_path"
      :alt="tvData.title"
    />
    <p>{{ tvData.name }}</p>
    <p>{{ tvData.original_name }}</p>
    <p>{{ tvData.original_language }}</p>
    <p>{{ tvData.vote_average }}</p>
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

<script>
import langFlag from "vue-lang-code-flags";
export default {
  methods: {
    starScore(score) {
      return Math.round(score / 2);
    },
    checkLenght(text) {
      if (text.length < 300) {
        return text;
      } else {
        return text.slice(0, 300) + "...";
      }
    },
  },
  components: {
    langFlag,
  },
  props: {
    tvData: Object,
  },
};
</script>

<template>
  <!-- classe generale della card -->
  <div class="card">
    <!-- copertina -->
    <img
      v-if="tvData.poster_path"
      :src="`https://image.tmdb.org/t/p/w342` + tvData.poster_path"
      :alt="tvData.title"
    />
    <img v-else src="../assets/missing.png" alt="" />
    <!-- titolo tradotto -->
    <div>Titolo: {{ tvData.name }}</div>
    <!-- titolo originale -->
    <div>Titolo originale: {{ tvData.original_name }}</div>
    <!-- lingua originale -->
    <div>
      <span>Lingua:</span>
      <langFlag :iso="tvData.original_language" />
    </div>
    <!-- score -->
    <div>
      <span>Score: </span>
      <span v-for="index in starScore(tvData.vote_average)" :key="index">
        <i class="fa-solid fa-star"></i>
      </span>
      <span v-for="index in 5 - starScore(tvData.vote_average)" :key="index">
        <i class="fa-regular fa-star"></i>
      </span>
    </div>
    <!-- descrizone -->
    <div>Overview: {{ checkLenght(tvData.overview) }}</div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: 300px;
  background-color: rgb(58, 58, 58);
  margin-bottom: 2em;

  img {
    width: 250px;
  }
}
</style>

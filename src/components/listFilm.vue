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
    filmData: Object,
  },
};
</script>

<template>
  <!-- classe generale della card -->
  <div class="card">
    <!-- locandina -->
    <img
      v-if="filmData.poster_path"
      :src="`https://image.tmdb.org/t/p/w342` + filmData.poster_path"
      :alt="filmData.title"
    />
    <img v-else src="../assets/missing.png" alt="" />
    <!-- titolo tradotto -->
    <div>Titolo: {{ filmData.title }}</div>
    <!-- titolo originale -->
    <div>Titolo originale: {{ filmData.original_title }}</div>
    <!-- lingua -->
    <div>
      <span>Lingua:</span>
      <langFlag :iso="filmData.original_language" />
    </div>
    <!-- score -->
    <div>
      <span>Score: </span>
      <span v-for="index in starScore(filmData.vote_average)" :key="index">
        <i class="fa-solid fa-star"></i>
      </span>
      <span v-for="index in 5 - starScore(filmData.vote_average)" :key="index">
        <i class="fa-regular fa-star"></i>
      </span>
    </div>
    <!-- descrzione -->
    <div>Overview: {{ checkLenght(filmData.overview) }}</div>
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

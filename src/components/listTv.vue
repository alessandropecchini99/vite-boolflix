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
    <div class="info">
      <!-- titolo tradotto -->
      <div>Titolo: {{ tvData.name }}</div>
      <!-- titolo originale -->
      <div>Titolo originale: {{ tvData.original_name }}</div>
      <!-- lingua originale -->
      <div>
        <span>Lingua :</span>
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
  </div>
</template>

<style lang="scss" scoped>
.card {
  cursor: default;
  height: 513px;
  background-color: black;
  margin-bottom: 2em;
  position: relative;

  .stars {
    color: yellow;
  }

  img {
    transition: 0.2s ease;
  }

  .info {
    opacity: 0;
    padding: 1em;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    transition: 0.3s ease;
  }

  &:hover img {
    opacity: 0;
  }

  &:hover .info {
    opacity: 1;
  }
}
</style>

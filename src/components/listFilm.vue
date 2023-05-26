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
    <!-- classe delle info -->
    <div class="info">
      <!-- titolo tradotto -->
      <div>Titolo: {{ filmData.title }}</div>
      <!-- titolo originale -->
      <div v-show="filmData.original_title !== filmData.title">
        Titolo originale: {{ filmData.original_title }}
      </div>
      <!-- lingua -->
      <div>
        <span>Lingua: </span>
        <langFlag :iso="filmData.original_language" />
      </div>
      <!-- score -->
      <div>
        <span>Score: </span>
        <span
          class="stars"
          v-for="index in starScore(filmData.vote_average)"
          :key="index"
        >
          <i class="fa-solid fa-star"></i>
        </span>
        <span
          class="stars"
          v-for="index in 5 - starScore(filmData.vote_average)"
          :key="index"
        >
          <i class="fa-regular fa-star"></i>
        </span>
      </div>
      <!-- descrzione -->
      <div>Overview: {{ checkLenght(filmData.overview) }}</div>
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
    font-size: 1.2em;
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

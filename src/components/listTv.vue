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
      :alt="tvData.name"
    />
    <img v-else src="../assets/missing.png" alt="" />
    <!-- classe delle info -->
    <div class="info">
      <!-- titolo tradotto -->
      <div>Titolo: {{ tvData.name }}</div>
      <!-- titolo originale -->
      <div v-show="tvData.original_name !== tvData.name">
        Titolo originale: {{ tvData.original_name }}
      </div>
      <!-- lingua originale -->
      <div>
        <span>Lingua :</span>
        <langFlag :iso="tvData.original_language" />
      </div>
      <!-- score -->
      <div>
        <span>Score: </span>
        <span
          class="stars"
          v-for="index in starScore(tvData.vote_average)"
          :key="index"
        >
          <i class="fa-solid fa-star"></i>
        </span>
        <span
          class="stars"
          v-for="index in 5 - starScore(tvData.vote_average)"
          :key="index"
        >
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
    transition: 0.4s ease;
    height: 513px;
    width: 342px;
  }

  .info {
    opacity: 0;
    padding: 1em;
    font-size: 1.2em;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    transition: 0.6s ease;

    div {
      padding-top: 8px;
    }
  }

  &:hover img {
    opacity: 0.1;
  }

  &:hover .info {
    opacity: 1;
  }
}
</style>

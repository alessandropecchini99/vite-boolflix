<script>
import listFilm from "./listFilm.vue";
import listTv from "./listTv.vue";

import { store } from "../store";

export default {
  data() {
    return {
      store,
    };
  },
  components: {
    listFilm,
    listTv,
  },
};
</script>

<template>
  <div class="background">
    <h3>FILM</h3>
    <div class="container">
      <listFilm
        v-for="film in store.arrFilm"
        :key="film.id"
        :filmData="film"
        class="prova"
      />
    </div>

    <h3>SERIE TV</h3>
    <div class="container">
      <listTv v-for="tv in store.arrTv" :key="tv.id" :tvData="tv" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.background {
  background: rgb(0, 0, 0);
  background: linear-gradient(
    180deg,
    rgba(0, 0, 0, 1) 0%,
    rgba(68, 68, 68, 1) 8%,
    rgba(113, 113, 113, 1) 74%,
    rgba(142, 142, 142, 1) 100%
  );

  h3 {
    padding-top: 3em;
    padding-bottom: 0.5em;
    margin-left: 1em;
    font-weight: 400;
  }

  .container {
    display: flex;
    gap: 0.2em;
    overflow-x: auto;
    padding-left: 1em;
  }
}
</style>

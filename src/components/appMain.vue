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
  <div class="info">
    film trovati: {{ store.arrFilm.length }} - tv series trovate:
    {{ store.arrTv.length }}
  </div>
  <h4>FILM</h4>
  <div class="container">
    <listFilm v-for="film in store.arrFilm" :key="film.id" :filmData="film" />
  </div>

  <h4>Tv Series</h4>
  <div class="container">
    <listTv v-for="tv in store.arrTv" :key="tv.id" :tvData="tv" />
  </div>
</template>

<style lang="scss" scoped>
@use "./../assets/variables.scss" as *;
.info {
  @include myContainer;
}
.container {
  background-color: rgb(177, 177, 177);
  display: flex;
  gap: 0.2em;
  overflow-x: auto;
  padding-left: 1em;
}
</style>

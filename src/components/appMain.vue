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
  <div class="containerFilm">
    <h4>FILM</h4>
    <listFilm v-for="film in store.arrFilm" :key="film.id" :filmData="film" />
  </div>

  <div class="containerTv">
    <h4>Tv Series</h4>
    <listTv v-for="tv in store.arrTv" :key="tv.id" :tvData="tv" />
  </div>
</template>

<style lang="scss" scoped>
@use "./../assets/variables.scss" as *;
.info {
  @include myContainer;
}
.containerFilm {
  background-color: rgb(177, 177, 177);
  display: flex;
  overflow-x: auto;
}
.containerTv {
  background-color: rgb(133, 133, 133);
  display: flex;
  overflow-x: auto;
}
</style>

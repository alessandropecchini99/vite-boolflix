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
h3 {
  padding-top: 3em;
  padding-bottom: 0.5em;
  margin-left: 1em;
  font-weight: 400;
}

.container {
  display: flex;
  gap: 0.05em;
  overflow-x: auto;
  scrollbar-width: thin;
  scrollbar-color: transparent transparent;
  padding-left: 1em;
}
</style>

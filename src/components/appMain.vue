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
  <main>
    <h2 v-if="store.arrFilm.length === 0 && store.arrTv.length === 0">
      OPS... NON ABBIATO TROVATO QUELLO CHE CERCHI
    </h2>

    <h3 v-show="store.arrFilm != ``">FILM</h3>
    <div class="container">
      <listFilm
        v-for="film in store.arrFilm"
        :key="film.id"
        :filmData="film"
        class="prova"
      />
    </div>

    <h3 v-show="store.arrTv != ``">SERIE TV</h3>
    <div class="container">
      <listTv v-for="tv in store.arrTv" :key="tv.id" :tvData="tv" />
    </div>
  </main>
</template>

<style lang="scss" scoped>
main {
  width: 100%;
  height: 100%;
  overflow-x: hidden;

  h2 {
    padding-top: 3em;
    padding-bottom: 0.5em;
    text-align: center;
    font-weight: 400;
  }

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

  .container::-webkit-scrollbar {
    display: none;
  }
}
</style>

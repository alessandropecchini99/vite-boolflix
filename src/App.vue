<script>
import appHeader from "./components/appHeader.vue";
import appMain from "./components/appMain.vue";

import axios from "axios";
import { store } from "./store";

export default {
  name: "App",
  data() {
    return {
      store,
    };
  },
  components: {
    appHeader,
    appMain,
  },
  methods: {
    loadApi() {
      // carico film nell'array
      axios
        .get(`https://api.themoviedb.org/3/search/movie`, {
          params: {
            api_key: "0260e91d337207be1aae7f6586ed01a8",
            query: this.store.searchFilm,
          },
        })
        .then((response) => (this.store.arrFilm = response.data.results));

      // carico serie tv nell'array
      axios
        .get(`https://api.themoviedb.org/3/search/tv`, {
          params: {
            api_key: "0260e91d337207be1aae7f6586ed01a8",
            query: this.store.searchFilm,
          },
        })
        .then((response) => (this.store.arrTv = response.data.results));
      console.log(store.arrFilm);
    },
  },
  created() {
    // inserisco dati al caricamento della pagina
    axios
      .get("https://api.themoviedb.org/3/movie/top_rated", {
        params: {
          api_key: "0260e91d337207be1aae7f6586ed01a8",
        },
      })
      .then((response) => (this.store.arrFilm = response.data.results));
    axios
      .get("https://api.themoviedb.org/3/tv/top_rated", {
        params: {
          api_key: "0260e91d337207be1aae7f6586ed01a8",
        },
      })
      .then((response) => (this.store.arrTv = response.data.results));
  },
};
</script>

<template>
  <appHeader @performSearch="loadApi" />

  <main>
    <appMain />
  </main>
</template>

<style lang="scss">
@use "./assets/general.scss" as *;
</style>

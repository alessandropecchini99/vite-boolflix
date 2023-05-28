<script>
// FEATURES AGGIUNTIVE:
// 1- il logo riporta alla home e pulisce l'input
// 2- l'input non accetta un valore vuoto o con solo spazi

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
      if (store.searchFilm.trim() === ``) {
        store.checkSearch = false;
        store.searchFilm = ``;
      } else {
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
        store.checkSearch = true;
      }
    },
    returnHome() {
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
      store.searchFilm = ``;
      store.checkSearch = true;
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
  <appHeader @performSearch="loadApi" @mainHome="returnHome" />
  <appMain />
</template>

<style lang="scss">
@use "./assets/general.scss" as *;
</style>

<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
  methods: {
    onSearch() {
      this.$emit(`performSearch`);
    },
    home() {
      this.$emit(`mainHome`);
    },
  },
};
</script>

<template>
  <header>
    <div class="navbar">
      <img @click="home" src="../assets/logo.png" alt="logo" />
      <div class="search">
        <span v-if="this.store.checkSearch == false" class="alert">
          Inserisci un titolo!
        </span>
        <div class="bordo">
          <input
            type="text"
            placeholder="Cerca un film o una serie"
            v-model="store.searchFilm"
            @keyup.enter="onSearch"
          />
          <button @click="onSearch">
            <i class="fa-solid fa-magnifying-glass"></i>
          </button>
        </div>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  height: 8vh;

  .navbar {
    width: 90%;
    height: 100%;
    margin-inline: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      cursor: pointer;
      height: 50px;
    }

    .search {
      display: flex;
      align-items: center;

      .alert {
        color: red;
        margin-right: 10px;
      }

      .bordo {
        border: 2px rgb(195, 0, 0) solid;
        input {
          width: 180px;
          outline: none;
          border: 0;
          padding: 5px;
          background-color: black;
          color: white;
        }

        button {
          background-color: rgb(195, 0, 0);
          color: white;
          border: 0;
          padding: 5px 10px;
          cursor: pointer;
        }
      }
    }
  }
}
</style>

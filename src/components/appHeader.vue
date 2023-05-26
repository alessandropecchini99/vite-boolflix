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
      <h1 @click="home">BOOLFLIX</h1>
      <div class="search">
        <span v-if="this.store.checkSearch == false" class="alert"
          >Inserisci un titolo!</span
        >
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
  background-color: black;
  height: 8vh;

  .navbar {
    width: 90%;
    height: 100%;
    margin-inline: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;

    h1 {
      color: rgb(195, 0, 0);
      cursor: pointer;
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

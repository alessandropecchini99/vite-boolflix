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
  },
};
</script>

<template>
  <header>
    <div class="navbar">
      <h1>BOOLFLIX</h1>
      <div>
        <input
          type="text"
          placeholder="Cerca un film"
          v-model="store.searchFilm"
          @keyup.enter="onSearch"
        />
        <button @click="onSearch">
          <i class="fa-solid fa-magnifying-glass"></i>
        </button>
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  background-color: black;
  height: 6vh;
  .navbar {
    width: 90%;
    height: 100%;
    margin-inline: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;

    h1 {
      color: rgb(195, 0, 0);
    }

    div {
      input {
        outline: none;
        border: 0;
        padding: 5px;
      }

      button {
        background-color: rgb(195, 0, 0);
        color: white;
        border: 0px;
        padding: 5px;
        &:hover {
          background-color: rgb(146, 0, 0);
        }
      }
    }
  }
}
</style>

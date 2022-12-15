<script>
// Imported components
import AppHeader from './components/AppHeader.vue'
import AppNav from "./components/AppNav.vue"
import AppMain from './components/AppMain.vue'
// Imported JS
import axios, { isCancel, AxiosError } from 'axios';
import { store } from "./store.js"

export default {

  // Registered components
  components: {
    AppHeader,
    AppNav,
    AppMain,
  },

  // App Data
  data() {
    return {
      store,
      title: "Breaking Bad API",
      remoteURL: "https://rickandmortyapi.com/api/character",
    };
  },

  methods: {

    // Filter events handlers
    filterRemove(){
      store.filter = undefined;
      this.filterUpdate();
    },

    filterUpdate(){
      console.log("Filter updated");
      this.loadCharacters();
    },

    // Character loading
    loadCharacters() {

      // Clear grid
      store.characters = [];

      // Fetch characters data
      axios
        .get(
          /* base call */
          this.remoteURL +
          /* filtered call */
          (store.filter != undefined ? `/?status=${store.filter}` : "")
        )
        .then((res) => {
          store.characters = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        })
    },
  },

  mounted() {
    this.loadCharacters();
  },
}
</script>

<template>
  <AppHeader :title="title" />
  <AppNav 
  @filterUpdate="this.filterUpdate"
  @filterRemove="this.filterRemove"/>
  <AppMain />
</template>

<style lang="scss">
@use "styles/general.scss";
@use "styles/partials/_palette.scss";

body {
  background-color: palette.$primary;
}
</style>

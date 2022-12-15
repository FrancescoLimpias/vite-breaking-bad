<script>

// Imported components
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
// Imported JS
import axios, { isCancel, AxiosError } from 'axios';
import { store } from "./store.js"

export default {

  // Registered components
  components: {
    AppHeader,
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

  mounted() {

    // Fetch characters data
    axios
      .get(this.remoteURL)
      .then((res) => {
        store.characters = res.data.results;
      })
      .catch((err) => {
        console.log("Yo man that's not cool");
      });
  },
}
</script>

<template>
  <AppHeader :title="title" />
  <AppMain />
</template>

<style lang="scss">
@use "styles/general.scss";
@use "styles/partials/_palette.scss";

body {
  background-color: palette.$primary;
}
</style>

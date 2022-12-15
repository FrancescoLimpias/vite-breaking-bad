<script>
import { store } from "../store.js";
import CharCard from "./CharCard.vue";

export default {

  components: {
    CharCard,
  },

  data() {
    return {
      store,
    }
  },
}

</script>

<template>
  <div class="container">

    <!-- Enum div (shows number of characters found) -->
    <div class="enum">
      Found {{ store.characters.length }} characters
    </div>

    <!--  -->
    <br>

    <!-- Grid ul -->
    <ul class="grid">
      <li v-for="(char, index) in store.characters">
        <CharCard :char="char" :index="index" />
      </li>
    </ul>

  </div>
</template>

<style lang="scss" scoped>
@use '../styles/partials/_palette.scss';

.container {
  background-color: white;
  max-width: 1270px;
  margin: 0 auto;
  padding: 2rem;
  .enum {
    background-color: palette.$secondary;
    color: white;
    padding: 1rem;
    font-weight: 400;
  }

  ul {
    // List style strip
    list-style-type: none;
    margin: 0;
    padding: 0;

    // Flex
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 1em;

    li {
      flex: 0 0 18%;
    }
  }
}
</style>

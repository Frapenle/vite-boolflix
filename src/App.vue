<script>
import { store } from "./store.js";
import HeaderComponent from './components/HeaderComponent.vue';
import axios from 'axios';

export default {
  components: {
    HeaderComponent,
  },

  data() {
    return {
      store,
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      apiKey: '608d618b027efbcefdc264f920beae3a',
    }
  },

  methods: {
    getMovies() {
      axios.get(this.apiUrl, {
        params: {
          api_key: this.apiKey,
          query: this.store.searchText,
        }
      })
        .then((response) => {
          console.log(response.data.results);
          this.store.movies = response.data.results;
        })
        .catch(function (error) {
          console.warn(error);
        });

    }
  },

  created() {
    // this.getMovies();
  },
}
</script>

<template>
  <HeaderComponent @search="getMovies" />
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>

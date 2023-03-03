<script>
import { store } from "./store.js";
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from "./components/MainComponent.vue";
import MovieComponent from './components/MovieComponent.vue';
import TvSeriesComponent from './components/TvSeriesComponent.vue';
import CArdComponent from './components/CardComponent.vue'

import axios from 'axios';

export default {
  components: {
    HeaderComponent,
    MainComponent,
    MovieComponent,
    TvSeriesComponent,
    CArdComponent,

  },

  data() {
    return {
      store,
      apiUrlMovie: 'https://api.themoviedb.org/3/search/movie',
      apiUrlTvSeries: 'https://api.themoviedb.org/3/search/tv',
      apiKey: '608d618b027efbcefdc264f920beae3a',
      languageDefault: 'it-IT'
    }
  },

  methods: {
    getMovies() {
      axios.get(this.apiUrlMovie, {
        params: {
          api_key: this.apiKey,
          query: this.store.searchText,
          language: this.languageDefault,
        }
      })
        .then((response) => {
          console.log(response.data.results);
          this.store.movies = response.data.results;
        })
        .catch(function (error) {
          console.warn(error);
        });

    },

    getTvSeries() {
      axios.get(this.apiUrlTvSeries, {
        params: {
          api_key: this.apiKey,
          query: this.store.searchText,
        }
      })
        .then((response) => {
          console.log(response.data.results);
          this.store.tvSeries = response.data.results;
        })
        .catch(function (error) {
          console.warn(error);
        });

    },
    searchMoviesAndSeries() {
      this.getMovies();
      this.getTvSeries();
    }
  },

  created() {
  },
}
</script>

<template>
  <HeaderComponent class="header position-fixed" @search="searchMoviesAndSeries" />
  <MainComponent />
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;

.header {
  z-index: 2;
}
</style>

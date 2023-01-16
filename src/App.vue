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
      apiUrl: 'https://api.themoviedb.org/3/movie',
      apiKey: '608d618b027efbcefdc264f920beae3a',
      queryString: 'Harry',

    }
  },

  methods: {
    getMovies() {
      axios.get(this.apiUrl, {
        params: {
          api_key: this.apiKey,
          query: this.queryString,
        }
      })
        .then((response) => {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });

    }
  },

  created() {
    this.getMovies();
  },
}
</script>

<template>
  <HeaderComponent />
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>

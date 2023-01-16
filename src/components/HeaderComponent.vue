<script>
import { store } from "../store";

export default {
  name: 'HeaderComponent',
  data() {
    return {
      store,

    }
  },
}

</script>

<template>
  <header>
    <h1>Header</h1>
    <label class="me-2" for="searchbar">Cerca</label>
    <input type="text" name="" id="searchbar" v-model="store.searchText">
    <button class="btn btn-danger ms-2" @keyup.enter="$emit('search')">Cerca</button>
    <ul>
      <li v-for="movie in store.movies" key="movie.id" class="mb-5">
        <h3>{{ movie.title }}</h3>
        <h4>{{ movie.original_title }}</h4>
        <p>Lingua {{ movie.original_language }} Voto: {{ movie.vote_average }}</p>
      </li>
    </ul>

  </header>
</template>

<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>

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
    <input type="text" name="" placeholder="Inserire titolo" id="searchbar" v-model="store.searchText"
      @keyup.enter="$emit('search')">
    <button class="btn btn-danger ms-2" @click="$emit('search')">Cerca</button>
    <ul>
      <li>
        <h2>Film</h2>
      </li>
      <li v-for="movie in store.movies" :key="movie.id" class="mb-5">
        <h3>{{ movie.title }}</h3>
        <h4>{{ movie.original_title }}</h4>
        <p>Lingua {{ movie.original_language }} Voto: {{ movie.vote_average }}</p>
      </li>
    </ul>

    <ul>
      <li>
        <h2>Serie TV</h2>
      </li>
      <li v-for="serie in store.tvSeries"> {{ serie.name }}</li>
    </ul>

  </header>
</template>

<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>

<script>
import { store } from "../store";

export default {
  name: 'HeaderComponent',
  data() {
    return {
      store,
      coverPath: 'https://image.tmdb.org/t/p/',
      coverDimension: 'w342',

    }
  },
}

</script>

<template>
  <header class="container-fluid">
    <h1>Header</h1>
    <label class="me-2" for="searchbar">Cerca</label>
    <input type="text" name="" placeholder="Inserire titolo" id="searchbar" v-model="store.searchText"
      @keyup.enter="$emit('search')">
    <button class="btn btn-danger ms-2" @click="$emit('search')">Cerca</button>
    <!-- <h3>Film</h3>
    <ul>
      <li v-for="movie in store.movies" :key="movie.id" class="mb-5 card">
        <div class="img-wrapper">
          <img :src="`${coverPath}${coverDimension}${movie.poster_path}`" :alt="movie.title" class="card-img-top">
        </div>
        <div class="card-body">
          <h5>{{ movie.title }}</h5>
          <h6>{{ movie.original_title }}</h6>
          <p>Lingua {{ movie.original_language }} - Voto: {{ movie.vote_average }}</p>
        </div>
      </li>
    </ul>

    <h3>Serie TV</h3>
    <ul>
      <li v-for="serie in store.tvSeries" :key="serie.id" class="mb-5 card">
        <div class="img-wrapper">
          <img :src="`${coverPath}${coverDimension}${serie.poster_path}`" :alt="serie.name" class="card-img-top">
        </div>
        <div class="card-body">
          <h5>{{ serie.name }}</h5>
          <h6>{{ serie.original_name }} </h6>
          <p>Lingua {{ serie.original_language }} - Voto: {{ serie.vote_average }}</p>
        </div>
      </li>
    </ul> -->

  </header>
</template>

<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>

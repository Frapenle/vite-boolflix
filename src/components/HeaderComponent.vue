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
    <div class="logo">
      <img src="../assets/img/logo.svg" alt="Netflix logo">
    </div>
    <div class="search">
      <input type="text" name="" placeholder="Inserire titolo" id="searchbar" v-model="store.searchText"
        @keyup.enter="$emit('search')">
      <button class="btn btn-danger ms-2" @click="$emit('search')">Cerca</button>
    </div>

  </header>
</template>

<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;

header {
  width: 100%;
  height: 70px;
  display: flex;
  background-color: black;
  align-items: center;
  justify-content: space-between;
}

.logo {
  width: 100px;

  img {
    width: 100%;
  }
}

.search {}
</style>

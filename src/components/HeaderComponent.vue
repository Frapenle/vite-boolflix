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
    <input type="text" name="" id="searchbar">
    <button class="btn btn-danger ms-2">Cerca</button>
    <ul>
      <li></li>
    </ul>

  </header>
</template>

<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;
</style>

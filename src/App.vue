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
      store

    }
  },
}
</script>

<template>
  <HeaderComponent />
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partials/variables.scss" as *;
</style>

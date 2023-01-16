<script>
import HeaderComponent from './components/HeaderComponent.vue';
import axios from 'axios';

export default {
  components: {
    HeaderComponent,
  }
}
</script>

<template>
  <HeaderComponent />
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "./styles/partialns/variables.scss" as *;
</style>

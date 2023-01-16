<script>
import HeaderComponent from './components/HeaderComponent.vue';

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
@use "./styles/partials/variables.scss" as *;
</style>

<script>
import MovieComponent from './MovieComponent.vue';
import TvSeriesComponent from './TvSeriesComponent.vue';
export default {
    name: 'MainComponent',
    components: {
        MovieComponent,
        TvSeriesComponent,
    },
    data() {
        return {

        }
    },

}
</script>

<template lang="">
    <main>
        <MovieComponent />
        <TvSeriesComponent />
        
    </main>
</template>
<style lang="scss" scoped>
main {
    padding-top: 75px;
}
</style>
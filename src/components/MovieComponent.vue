<template lang="">
    <section v-if="store.movies != false" class="films">
        <h3>Film</h3>
        <ul class="items-container">
            <li v-for="movie in store.movies" :key="movie.id" class="mb-5 card">
                <CardComponent 
                :posterPath="movie.poster_path"
                :title="movie.title"
                :originalTitle="movie.original_title"
                :language="movie.original_language"
                :avRating="movie.vote_average"
                :overview="movie.overview"
                />
            </li>
        </ul>
    </section>
    <p v-else>Nessun risultato per la tua ricerca nei Films</p>
</template>
<script>
import { store } from "../store";
import CardComponent from './CardComponent.vue';


export default {
    name: 'MovieComponent',
    components: {
        CardComponent,
    },
    data() {
        return {
            store,

        }
    },


}
</script>
<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;

.items-container {
    display: flex;
    flex-wrap: wrap;
    gap: .2rem;
}

.card {
    width: calc(100% / 4 - .2rem);
    position: relative;
    cursor: pointer;
    transition: transform 500ms;
}

.card:focus,
.card:hover {
    transform: scale(1.1);
    z-index: 1;
}
</style>
<template lang="">
    <section class="films">
        <h3>Film</h3>
        <ul>
            <li v-for="movie in store.movies" :key="movie.id" class="mb-5 card">
                <div class="img-wrapper">
                    <img :src="`${coverPath}${coverDimension}${movie.poster_path}`" :alt="movie.title" class="card-img-top">
                </div>
                <div class="card-body">
                    <h5>{{ movie.title }}</h5>
                    <h6>{{ movie.original_title }}</h6>
                    <p>Lingua {{ movie.original_language }} - Voto: {{ Math.floor(movie.vote_average / 2)}}</p>
                    <div class="ratings">
                        <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(movie.vote_average / 2)"/>
                        <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (movie.vote_average / 2))"/>
                    </div>
                </div>
            </li>
        </ul>
    </section>
</template>
<script>
import { store } from "../store";

export default {
    name: 'MovieComponent',
    data() {
        return {
            store,
            coverPath: 'https://image.tmdb.org/t/p/',
            coverDimension: 'w342',

        }
    },

}
</script>
<style lang="scss" scoped>
@use "../styles/general.scss" as *;
@use "../styles/partials/variables.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;

ul {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
}

.card {
    width: calc(100% / 5 - 1rem);
}

.img-wrapper {}

img {}
</style>
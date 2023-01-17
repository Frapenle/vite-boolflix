<template lang="">
    <section class="films">
        <h3>Film</h3>
        <ul>
            <li v-for="movie in store.movies" :key="movie.id" class="mb-5 card">
                <div class="img-wrapper">
                    <img v-if="movie.poster_path != null" :src="`${coverPath}${coverDimension}${movie.poster_path}`" :alt="movie.title" class="card-img-top">
                    <img v-else src="http://www.tecno-store.it/wp-content/uploads/immagine-non-disponibile-q.png" alt="" class="fakeimg">

                </div>
                <div class="card-body">
                    <h5 v-if="movie.title != movie.original_title">{{ movie.title }}</h4>
                    <h5 v-else>{{ movie.original_title }}</h5>
                    <div class="language">Lingua:
                        <img v-if="langFlags.includes(movie.original_language)" :src="getImagePath(movie.original_language)">
                        <span v-else>{{ movie.original_language }}</span>
                    </div>
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
            langFlags: ['en', 'it', 'fr', 'usa'],

        }
    },
    methods: {
        getImagePath: function (img) {
            return new URL(`../assets/img/${img}.png`, import.meta.url).href;
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

.fakeimg {
    width: 100%;
}

.language>img {
    width: 30px;
}
</style>
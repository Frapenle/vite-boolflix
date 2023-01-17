<template lang="">
    <section class="films">
        <h3>Serie TV</h3>
        <ul>
            <li v-for="serie in store.tvSeries" :key="serie.id" class="mb-5 card">
                <div class="img-wrapper">
                    <img v-if="serie.poster_path != null" :src="`${coverPath}${coverDimension}${serie.poster_path}`" :alt="serie.name" class="card-img-top">
                    <img v-else src="http://www.tecno-store.it/wp-content/uploads/immagine-non-disponibile-q.png" :alt="serie.name" class="fakeimg">

                </div>
                <div class="card-body">
                    <h6 v-if="serie.name != serie.original_name">{{ serie.name }}</h6>
                    <h6 v-else>{{ serie.original_name }} </h6>
                    <div class="language">Lingua:
                        <img v-if="langFlags.includes(serie.original_language)" :src="getImagePath(serie.original_language)">
                        <span v-else>{{ serie.original_language }}</span>
                    </div>
                    <div class="ratings">
                        <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(serie.vote_average / 2)"/>
                        <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (serie.vote_average / 2))"/>
                    </div>
                </div>
            </li>
        </ul>
    </section>
</template>
<script>
import { store } from "../store";

export default {
    name: 'TvSeriesComponent',
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

ul.items-container {
    display: flex;
    flex-wrap: wrap;
    gap: .2rem;
}

.card {
    width: calc(100% / 5 - .2rem);
    position: relative;
    cursor: pointer;
    transition: transform 500ms;
}

ul:focus-within .card,
ul:hover .card {
    transform: translateX(-10%);
}

.card:focus~.card,
.card:hover~.card {
    transform: translateX(10%);
}

ul .card:focus,
ul .card:hover {
    transform: scale(1.2);
    z-index: 1;
}

.card-img-top {
    height: 25vw;
    object-fit: cover;
}

.fakeimg {
    width: 100%;
}

.language>img {
    width: 30px;
}
</style>
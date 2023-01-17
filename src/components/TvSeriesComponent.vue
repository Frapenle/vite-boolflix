<template lang="">
    <section class="films">
        <h3>Serie TV</h3>
        <ul>
            <li v-for="serie in store.tvSeries" :key="serie.id" class="mb-5 card">
                <div class="img-wrapper">
                    <img v-if="serie.poster_path != null" :src="`${coverPath}${coverDimension}${serie.poster_path}`" :alt="serie.name" class="card-img-top">
                    <img v-else src="http://www.tecno-store.it/wp-content/uploads/immagine-non-disponibile-q.png" alt="" class="fakeimg">

                </div>
                <div class="card-body">
                    <h5>{{ serie.name }}</h5>
                    <h6>{{ serie.original_name }} </h6>
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

.img-wrapper {}

img {}
</style>
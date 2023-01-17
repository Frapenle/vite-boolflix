<template lang="">
    <section v-if="store.tvSeries != false" class="films">
        <h3>Serie TV</h3>
        <ul class="items-container">
            <li v-for="serie in store.tvSeries" :key="serie.id" class="mb-5 card">
                <div class="img-wrapper">
                    <img v-if="serie.poster_path != null" :src="`${coverPath}${coverDimension}${serie.poster_path}`" :alt="serie.name" class="card-img-top cover-img">
                    <img v-else src="http://www.tecno-store.it/wp-content/uploads/immagine-non-disponibile-q.png" :alt="serie.name" class="fakeimg card-img-top">

                </div>
                <div class="hover">
                    <div class="title">
                        <p v-if="serie.name != serie.original_name"><span>Titolo: </span>{{ serie.name }}</p>
                        <p v-else><span>Titolo: </span> {{ serie.original_name }}</p>
                    </div>
                    <div class="overview">
                        <p><span>Overview: </span>{{ serie.overview }}</p>
                    </div>
                    <div class="language"><span>Lingua: </span>
                        <img v-if="langFlags.includes(serie.original_language)" :src="getImagePath(serie.original_language)">
                        <span v-else>{{ serie.original_language }}</span>
                    </div>
                    <div class="ratings"><span>Voto: </span>
                        <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(serie.vote_average / 2)"/>
                        <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (serie.vote_average / 2))"/>
                    </div>

                </div>
                <div class="card-body">
                    <h6 v-if="serie.name != serie.original_name">{{ serie.name }}</h6>
                    <h6 v-else>{{ serie.original_name }} </h6>
                    <!-- <div class="language">Lingua:
                        <img v-if="langFlags.includes(serie.original_language)" :src="getImagePath(serie.original_language)">
                        <span v-else>{{ serie.original_language }}</span>
                    </div> -->
                    <div class="ratings">
                        <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(serie.vote_average / 2)"/>
                        <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (serie.vote_average / 2))"/>
                    </div>
                </div>
            </li>
        </ul>
    </section>
    <p v-else>Nessun risultato per la tua ricerca nelle serie TV</p>
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


.items-container {
    display: flex;
    flex-wrap: wrap;
    gap: .2rem;
}

.img-wrapper {
    position: relative;
    width: 100%;
}

.img-wrapper>.cover-img {
    opacity: 1;
    display: block;
    width: 100%;
    height: auto;
    transition: .5s ease;
    backface-visibility: hidden;
}

.hover {
    height: 100%;
    padding: 1rem .5rem;
    padding: 1rem .5rem;
    transition: .5s ease;
    opacity: 0;
    position: absolute;
    top: 0;
    left: 0;

    p {
        font-size: .9rem;
    }

    span {
        font-weight: bold;
    }
}

.overview {
    height: 70%;
    overflow-y: auto;
}


.img-wrapper:hover .cover-img {
    opacity: 0.2;
}

.img-wrapper:hover .hover {
    opacity: 1;
}

.card {
    width: calc(100% / 5 - .2rem);
    position: relative;
    cursor: pointer;
    transition: transform 500ms;
}

ul .card:focus,
ul .card:hover {
    transform: scale(1.1);
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
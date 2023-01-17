<template lang="">
    <section v-if="store.movies != false" class="films">
        <h3>Film</h3>
        <ul class="items-container">
            <li v-for="movie in store.movies" :key="movie.id" class="mb-5 card">
                <div class="img-wrapper">
                    <img v-if="movie.poster_path != null" :src="`${coverPath}${coverDimension}${movie.poster_path}`" :alt="movie.title" class="cover-img card-img-top">
                    <img v-else src="http://www.tecno-store.it/wp-content/uploads/immagine-non-disponibile-q.png" :alt="movie.title" class="fakeimg card-img-top">
                    <div class="hover">
                        <div class="title">
                            <p v-if="movie.title != movie.original_title"><span>Titolo: </span>{{ movie.title }}</p>
                            <p v-else><span>Titolo: </span> {{ movie.original_title }}</p>
                        </div>
                        <div class="overview">
                            <p><span>Overview: </span>{{ movie.overview }}</p>
                        </div>
                        <div class="language"><span>Lingua: </span>
                            <img v-if="langFlags.includes(movie.original_language)" :src="getImagePath(movie.original_language)">
                            <span v-else>{{ movie.original_language }}</span>
                        </div>
                        <div class="ratings"><span>Voto: </span>
                            <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(movie.vote_average / 2)"/>
                            <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (movie.vote_average / 2))"/>
                        </div>

                    </div>
                </div>
                
                <div class="card-body">
                    <h6 v-if="movie.title != movie.original_title">{{ movie.title }}</h6>
                    <h6 v-else>{{ movie.original_title }}</h6>
                    <!-- <div class="language">Lingua:
                        <img v-if="langFlags.includes(movie.original_language)" :src="getImagePath(movie.original_language)">
                        <span v-else>{{ movie.original_language }}</span>
                    </div> -->
                    <div class="ratings">
                        <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(movie.vote_average / 2)"/>
                        <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (movie.vote_average / 2))"/>
                    </div>
                </div>
            </li>
        </ul>
    </section>
    <p v-else>Nessun risultato per la tua ricerca nei Films</p>
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

.card:focus,
.card:hover {
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
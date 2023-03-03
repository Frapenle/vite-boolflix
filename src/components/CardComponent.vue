<template lang="">
    <div>
        <div class="img-wrapper">
            <img v-if="posterPath != null" :src="`${coverPath}${coverDimension}${posterPath}`" :alt="title" class="cover-img card-img-top">
            <img v-else src="http://www.tecno-store.it/wp-content/uploads/immagine-non-disponibile-q.png" :alt="title" class="fakeimg card-img-top">
            <div class="hover">
                <div class="title">
                    <p v-if="title != originalTitle"><span>Titolo: </span>{{ title }}</p>
                    <p v-else><span>Titolo: </span> {{ originalTitle }}</p>
                </div>
                <div class="overview">
                    <p><span>Overview: </span>{{ overview }}</p>
                </div>
                <div class="language"><span>Lingua: </span>
                    <img v-if="langFlags.includes(language)" :src="getImagePath(language)">
                    <span v-else>{{ language }}</span>
                </div>
                <div class="ratings"><span>Voto: </span>
                    <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(avRating / 2)"/>
                    <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (avRating / 2))"/>
                </div>

            </div>
        </div>
                
        <div class="card-body">
            <h6 v-if="title != originalTitle">{{ title }}</h6>
            <h6 v-else>{{ originalTitle }}</h6>
            <!-- <div class="language">Lingua:
                <img v-if="langFlags.includes(movie.original_language)" :src="getImagePath(movie.original_language)">
                <span v-else>{{ movie.original_language }}</span>
            </div> -->
            <div class="ratings">
                <font-awesome-icon icon="fa-solid fa-star" v-for="star in Math.floor(avRating / 2)"/>
                <font-awesome-icon icon="fa-regular fa-star" v-for="blank_star in Math.ceil(5 - (avRating / 2))"/>
            </div>
        </div>
        
    </div>
</template>
<script>
export default {
    name: 'CardComponent',
    props: ['posterPath', 'title', 'originalTitle', 'language', 'avRating', 'overview'],
    data() {
        return {
            langFlags: ['en', 'it', 'fr', 'usa'],
            coverPath: 'https://image.tmdb.org/t/p/',
            coverDimension: 'w342',
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

.card-img-top {
    height: 25vw;
    object-fit: cover;
}

.fakeimg {
    width: 100%;
}

.language>img {
    width: 20px;
}
</style>
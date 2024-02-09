<script>
import { posterImage } from '../data/index';
export default {
    name: 'ProductionCard',
    data: () => ({
        votes: [1, 2, 3, 4, 5],

    }),
    props: {
        media: Object,
        posterPath: String,
        imageName: String

    },
    computed: {
        hasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.media.original_language);
        },

        flagSrc() {
            const url = new URL(`../assets/img/${this.media.original_language}.png`, import.meta.url);
            return url.href;
        },

        starVote() {
            const vote = parseInt(this.media.vote_average / 2)
            return vote
        },

        posterSrc() {
            if (!this.posterPath) return posterImage.placeholder;
            return posterImage.baseUri + this.posterPath
        }





    }
}
</script>
<template>
    <div class="col media-card">
        <img class="poster-image" :src="posterSrc" :alt="imageName">

        <ul class="card-info-container">
            <li class="language-info mb-4">
                <img v-if="hasFlag" :src="flagSrc" alt="">
                <span v-else><strong>Lingua originale:</strong> {{ media.original_language }}</span>
            </li>
            <li class="mb-4"><strong>Titolo:</strong> {{ media.title || media.name }}</li>
            <li class="mb-4"><strong>Titolo originale:</strong> {{ media.original_title || media.original_name }}</li>
            <li>
                <ul class="d-flex">
                    <li v-for="vote in votes"> 
                        <i v-if="vote > starVote" class="fa-star fa-regular"></i>
                        <i v-else class="fa-star fa-solid"></i>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</template>

<style lang="scss" scoped>
.media-card {
    max-width: 342px;
    height: 513px;
    background-color: black;
    color: white;
    border: 1px solid red;
    padding: 0;

    .card-info-container {
        display: none;
        width: 342px;

        .fa-solid{
            color: yellow;
        }
    }

    &:hover {
        padding: 16px;
        .poster-image {
            display: none;
        }

        .card-info-container{
            display: block;
        }
    }


    .poster-image {
        height: 513px;
    }

    .language-info {
        height: 50px;

        img {
            height: 100%;
        }
    }

}
</style>


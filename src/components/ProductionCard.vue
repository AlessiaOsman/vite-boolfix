<script>
import { posterImage } from '../data/index';
export default {
    name: 'ProductionCard',
    data: () => ({
        votes: [1,2,3,4,5],
        
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

        starVote(){
            const vote = parseInt(this.media.vote_average / 2)
            return vote
        },

        posterSrc(){
            if (!this.posterPath) return posterImage.placeholder;
            return posterImage.baseUri + this.posterPath 
        }

        

        

    }
}
</script>
<template>
    
    <ul>
        <li>
            <img :src="posterSrc" :alt="imageName">
        </li>
        <li>{{ media.title || media.name }}</li>
        <li>{{ media.original_title || media.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" alt="">
            <span v-else>{{ media.original_language }}</span>
        </li>
        <li>{{ starVote }}</li>
        <li>
            <ul>
                <li v-for="vote in votes">
                    <i v-if="vote > starVote" class="fa-star fa-regular"></i>
                    <i v-else class="fa-star fa-solid"></i>
                </li>
            </ul>
        </li>
    </ul>
</template>


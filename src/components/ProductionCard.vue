<script>
export default {
    name: 'ProductionCard',
    props: {
        media: Object,

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
        }

    }
}
</script>
<template>
    
    <ul>
        <li>
            <img src="" alt="">
        </li>
        <li>{{ media.title || media.name }}</li>
        <li>{{ media.original_title || media.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" alt="">
            <span v-else>{{ media.original_language }}</span>
        </li>
        <li>
            {{ starVote }}
        </li>
    </ul>
</template>
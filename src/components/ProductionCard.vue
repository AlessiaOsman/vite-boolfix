<script>
export default {
    name: 'ProductionCard',
    data: () => ({
        votes: [1,2,3,4,5]
    }),
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
        },

        starIcons(className){
            for (let i = 1; i <= 5; i++) {
            if (i <= this.starVote) {
            className = 'fa-solid'
            } else {
            className = 'fa-regular'
        }
      }
      return className;
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
            <i class="fa-star" :class="starIcons"></i>
        </li>
    </ul>
</template>
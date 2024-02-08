<script>
export default {
    name: 'ProductionCard',
    props: {
        list: Object
    },
    computed: {
        hasFlag() {
            const flags = ['it', 'en'];
            return flags.includes(this.list.original_language);
        },

        flagSrc() {
            const url = new URL(`../assets/img/${this.list.original_language}.png`, import.meta.url);
            return url.href;
        }
    }
}
</script>
<template>
    <ul>
        <li>{{ list.title || list.name }}</li>
        <li>{{ list.original_title || list.original_name }}</li>
        <li>
            <img v-if="hasFlag" :src="flagSrc" alt="">
            <span v-else>{{ list.original_language }}</span>
        </li>
        <li>{{ list.vote_average }}</li>
    </ul>
</template>
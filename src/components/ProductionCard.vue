<script>
    export default {
        name: 'ProductionCard',
        props: {
            list: Object
        }
    }
</script>
<template>
        <ul>
            <li>{{ list.title || list.name }}</li>
            <li>{{ list.original_title || list.original_name }}</li>
            <li>{{ list.original_language }}</li>
            <li>{{ list.vote_average }}</li>
        </ul>
</template>
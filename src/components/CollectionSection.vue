<script>
    import ProductionCard from './ProductionCard.vue';
    export default {
        name: 'CollectionSection',
        props: {
            titleSection: String,
            collections: Array,
            title: String,

        },
        components: { ProductionCard, ProductionCard }
    }
</script>
<template>
    <section>
        <h1>{{ titleSection }}</h1>
        <ProductionCard  v-for="collection in collections" :list="collection"/>
    </section>

</template>
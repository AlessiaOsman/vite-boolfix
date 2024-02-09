<script>
    import ProductionCard from './ProductionCard.vue';
    export default {
        name: 'CollectionSection',
        props: {
            titleSection: String,
            collections: Array,

        },
        components: { ProductionCard, ProductionCard }
    }
</script>
<template>
    <section>
        <h1>{{ titleSection }}</h1>
        <ProductionCard  v-for="collection in collections" 
        :key="collection.id" 
        :media="collection"
        :posterPath="collection.poster_path"
        :imageName="collection.name || collection.title"
        />
    </section>

</template> 
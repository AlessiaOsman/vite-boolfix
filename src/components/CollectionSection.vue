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
    <section class="row justify-content-center">
        <h1 class="text-center">{{ titleSection }}</h1>
        <ProductionCard v-for="collection in collections" 
        :key="collection.id" 
        :media="collection"
        :posterPath="collection.poster_path"
        :imageName="collection.name || collection.title"
        />
    </section>

</template> 

<style lang="scss" scoped>
    section{
        &:first-child{
            margin-bottom: 32px;
        }
        h1{
            color: white;
            padding: 0;
            margin-bottom: 32px;
        }
    }
</style>
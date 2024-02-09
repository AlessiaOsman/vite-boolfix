<script>
    import BaseSearch from './search/BaseSearch.vue';
  export default {
    name: 'AppHeader',
    components: {BaseSearch},
    emits: ['search-data', 'set-text'],
    
  }
</script>

<template>
  <header class="d-flex justify-content-between align-items-center p-4">
    <h1>Boolfix</h1>
    <BaseSearch @text-change="$emit('set-text', $event)"  @submit-search="$emit('search-data')"/>
  </header>
</template>

<style lang="scss" scoped>
  header{
    position: sticky;
    top: 0;
    right: 0;
    left: 0;
    background-color: black;

    h1{
      color: red;
    }
    
  }
</style>


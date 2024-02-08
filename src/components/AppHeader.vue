<script>
    import BaseSearch from './search/BaseSearch.vue';
  export default {
    name: 'AppHeader',
    components: {BaseSearch},
    emits: ['search-data', 'set-text'],
    
  }
</script>

<template>
  <header>
    <h1>Boolfix</h1>
    <BaseSearch @text-change="$emit('set-text', $event)"  @submit-search="$emit('search-data')"/>
  </header>
</template>


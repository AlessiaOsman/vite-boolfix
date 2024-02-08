<script>
    import BaseSearch from './search/BaseSearch.vue';
  export default {
    name: 'AppHeader',
    components: {BaseSearch}
  }
</script>

<template>
  <header>
    <h1>Boolfix</h1>
    <BaseSearch @submit-search=""/>
  </header>
</template>


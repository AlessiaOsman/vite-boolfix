<script>
import axios from 'axios'
import { api } from './data/index.js'
import { store } from './data/store.js'
import CollectionSection from './components/CollectionSection.vue'
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  name: 'Boolfix',
  components: { AppMain, CollectionSection },
  data: () => ({
    store,
  }),
  components: { AppHeader, AppMain, CollectionSection },
  methods: {

    setText(text){
      store.filter = text
    },

    searchProduction() {
      if(!store.filter) {
        store.movies = []
        store.series = []
        return;
      } 

      this.fetchApi('search/movie', 'movies')
      this.fetchApi('search/tv', 'series')
  
    },
    fetchApi(endpoint, collection){
      const { baseUri, language, apiKey, baseUriImage } = api;
      const params = {
        query: store.filter,
        api_key: apiKey,
        language
      }
      axios.get(`${baseUri}/${endpoint}`, { params })
        .then((res) => {
          store[collection] = res.data.results;
        })
        .catch((err) => {
          console.error(err)
        })
    }



  }
}
</script>

<template>
  <AppHeader @search-data="searchProduction" @set-text="setText" />
  <AppMain>
    <CollectionSection titleSection="Movies" :collections="store.movies" />
    <CollectionSection titleSection="Series" :collections="store.series" />
  </AppMain>
</template>

<style lang="scss">
@use'./assets/scss/style.scss';
</style>
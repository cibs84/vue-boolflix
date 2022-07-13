<template>
  <div id="app">
      <HeaderComponent @search="searchMovies"/>

      <main>
          <MovieList :arrayPassed="moviesArray"/>
      </main>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComponent from './components/HeaderComponent.vue';
import MovieList from './components/MovieList.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MovieList
  },
  data(){
    return {
      transferCompleted: false,
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: '762e8d8371364239e7194e5712ca4d7b',
      moviesArray: [],
      seriesArray: [],
      allResults: []
    }
  },
  methods: {
    searchMovies(inputSearch){
        // Creo l'oggetto con i parametri per la chiamata
        const objParams = {
          params: {
            api_key: this.apiKey,
            query: inputSearch,
            language: 'it-IT'
          }
        }
        // Faccio partire le chiamate API passando i parametri alle funzioni
        this.getMovies(objParams);
        this.getSeries(objParams);
    },
    getMovies(apiParams){
        axios
        .get(this.apiUrl + 'movie', apiParams)
        .then((response) => {
            this.moviesArray = response.data.results;
            this.allResults = [...this.moviesArray, ...this.seriesArray];
            this.transferCompleted = true;
        }).catch(err => {
            console.log('Error: ', err)
        });
    },
    getSeries(apiParams){
        axios
        .get(this.apiUrl + 'tv', apiParams)
        .then((response) => {
            this.seriesArray = response.data.results;
            this.allResults = [...this.moviesArray, ...this.seriesArray];
            this.transferCompleted = true;
        }).catch(err => {
            console.log('Error: ', err)
        });
    }
  }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';
@import './assets/styles/variables.scss';
</style>
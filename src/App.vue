<template>
  <div id="app">
      <HeaderComponent @search="searchMovies"/>

      <main>
          <MovieList :searchText="searchText"/>
      </main>
  </div>
</template>

<script>
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
      searchText: ""
    }
  },
  methods: {
    searchMovies(inputSearch){
        this.searchText = inputSearch;
    }
  }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';
@import './assets/styles/variables.scss';
</style>

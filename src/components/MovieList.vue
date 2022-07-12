<template>
    <section class="movie-list">
        <div class="container">
            <div class="row row-cols-6">
                <div class="col" v-for="(singleMovie, index) in moviesArray" :key="index" :searchText="searchText">
                    <MovieCard 
                        :title="singleMovie.title" 
                        :originalTitle="singleMovie.original_title" 
                        :language="singleMovie.original_language" 
                        :vote="singleMovie.vote_average"
                    />
                </div>
            </div>
        </div>
    </section>
</template>


<script>
import MovieCard from './MovieCard.vue';
import axios from 'axios';

export default {
    name: 'MovieList',
    components: {
        MovieCard
    },
    props: {
        searchText: String
    },
    data(){
        return {
            transferCompleted: false,
            moviesArray: [],
            inputSearch: this.searchText
        }
    },
    methods: {
        getMovies(inputSearch){
            axios
            // .get('https://api.themoviedb.org/3/search/movie?api_key=762e8d8371364239e7194e5712ca4d7b&language=en-US&query=bat&page=1&include_adult=false')
            .get('https://api.themoviedb.org/3/search/movie', { 
                params: {
                    api_key: '762e8d8371364239e7194e5712ca4d7b',
                    query: inputSearch
                }
            })
            .then(response => {
                this.moviesArray = response.data.results;
                console.log(response);
                this.transferCompleted = true;
            })
            .catch(err => {
                console.log('Error: ', err)
            })
        }
    },
    created() {
        this.getMovies(this.searchText);
    }
}
</script>


<style lang="scss" scoped>

</style>
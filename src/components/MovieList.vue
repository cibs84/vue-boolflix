<template>
    <section class="movie-list">
        <div class="container">
            <div class="row row-cols-6">
                <div class="col" v-for="(singleMovie, index) in arrayPassed" :key="index" :arrayReturned="arrayPassed">
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


export default {
    name: 'MovieList',
    components: {
        MovieCard
    },
    props: {
        arrayPassed: Array
    },
    data(){
        return {
            moviesArray: []
        }
    },
    mounted(){
        () => {
            this.moviesArray = this.arrayPassed;
        }
    }
}
</script>


<style lang="scss" scoped>

</style>
<template>
    <section class="movie-list">
        <div class="container">
            <h2 class="title">Film in italiano</h2>
            <div class="row row-cols-6">
                <div class="col" v-for="(singleMovie, index) in arrayPassed" :key="index" :arrayReturned="arrayPassed">
                    <MsCard 
                        :title="singleMovie.title" 
                        :originalTitle="singleMovie.original_title" 
                        :language="singleMovie.original_language" 
                        :vote="singleMovie.vote_average"
                        :overview="singleMovie.overview"
                        :posterPath="singleMovie.poster_path"
                    />
                </div>
            </div>
        </div>
    </section>
</template>


<script>
import MsCard from './MsCard.vue';


export default {
    name: 'MovieList',
    components: {
        MsCard
    },
    props: {
        arrayPassed: Array
    }
}
</script>


<style lang="scss" scoped>

</style>
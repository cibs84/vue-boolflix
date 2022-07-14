<template>
    <section class="movie-list">
        <div class="container">
            <h2 class="title">Film in italiano</h2>
            <div class="row row-cols-6">
                <div 
                    class="col" 
                    v-for="(singleMovie, index) in arrayPassed" 
                    :key="index"
                >
                    <!-- MsCard Component -->
                    <MsCard :itemArray="singleMovie"/> 
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
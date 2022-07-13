<template>
    <section class="series-list">
        <div class="container">
            <h2 class="title">Serie TV da vedere tutto d'un fiato</h2>
            <div class="row row-cols-6">
                <div class="col" v-for="(singleSeries, index) in arrayPassed" :key="index" :arrayReturned="arrayPassed">
                    <MsCard 
                        :title="singleSeries.name" 
                        :originalTitle="singleSeries.original_name" 
                        :language="singleSeries.original_language" 
                        :vote="singleSeries.vote_average"
                        :overview="singleSeries.overview"
                        :posterPath="singleSeries.poster_path"
                    />
                </div>
            </div>
        </div>
    </section>
</template>


<script>
import MsCard from './MsCard.vue';


export default {
    name: 'SeriesList',
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
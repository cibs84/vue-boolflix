<template>
    <section class="series-list">
        <div class="container">
            <h2 class="title">Serie TV da vedere tutto d'un fiato</h2>
            <div class="row row-cols-6">
                <div 
                    class="col" 
                    v-for="(singleSeries, index) in arrayPassed" 
                    :key="index"
                >
                    <!-- MsCard Component -->
                    <MsCard :itemArray="singleSeries"/> 
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
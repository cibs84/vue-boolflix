<template>
    <!-- <div class="col"> -->
        <div class="ms_card">
            <ul>
                <li>{{title}}</li>
                <li>{{originalTitle}}</li>
                <li>{{language}}</li>
                <li>{{vote}}</li>
            </ul>
        </div>
    <!-- </div> -->
</template>


<script>
export default {
    name: 'MovieCard',
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number
    }
}
</script>


<style lang="scss" scoped>
.ms_card {
    border: 1px solid white;
    color: white;
    padding: 1rem;
    margin-bottom: 1.5rem;

}
</style>
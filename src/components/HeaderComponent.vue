<template>
    <header>
        <div class="container">
            <div class="row">
                <!-- Boolfix Title -->
                <img class="main-title" src="../assets/img/boolflix_logo.png" alt="logo boolfix">

                <!-- Search -->
                <div class="input-group search">
                    <input v-model="inputSearch" @keyup.enter="$emit('search', inputSearch)" type="text" class="form-control" placeholder="Titoli, persone, generi" aria-label="Search" aria-describedby="button-addon2">
                    <button @click="$emit('search', inputSearch)" class="btn btn-outline-secondary" type="button" id="button-addon2">Search</button>
                </div>
            </div>
        </div>
    </header>
</template>


<script>
export default {
    name: 'HeaderComponents',
    data() {
        return {
            inputSearch: ""
        }
    }
}
</script>


<style lang="scss" scoped>
@import '../assets/styles/variables.scss';

header {
    background-color: $bg_primary_color;
    padding: 2rem;

    .row {
        display: flex;
        justify-content: space-between;
        align-items: center;

        .main-title {
            color: $brand_primary_color;
            font-weight: 600;
            font-size: 2rem;
            width: 10rem;
            flex-grow: 0;
        }
        .search {
            flex-grow: 0;
            width: 50%;
    
            input {
                border-color: $brand_secondary_color;
                color: $brand_secondary_color;
                background-color: transparent;
            }
        }
    }
}
</style>
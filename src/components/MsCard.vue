<template>
    <div class="ms_card" :style="itemArray.poster_path ? stylePoster : stylePlaceholderPoster">
        <ul>
            <li>
                <span class="fw-bold">Titolo: </span>{{itemArray.title}}
            </li>
            <li>
                <span class="fw-bold">Titolo originale: </span>{{itemArray.original_title}}
            </li>
            <li>
                <span class="fw-bold">Original language: </span>
                <img class="flag" :src="`https://countryflagsapi.com/png/${this.fixFlag(itemArray.original_language)}`">
            </li>
            <li class="stars-container">
                <!-- Ciclo Stelline -->
                <span class="star " 
                    v-for="(number, index) in 5" 
                    :key="index" 
                    :class="{ 'active': number <= Math.ceil(itemArray.vote_average/2)}"
                >&#9733;</span>
            </li>
            <li>
                <span class="fw-bold">Overview: </span>
                {{itemArray.overview}}
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    name: 'MsCard',
    props: {
        itemArray: Array
    },
    data(){
        return {
            stylePoster: `background-image: url('https://image.tmdb.org/t/p/w342${this.itemArray.poster_path}')`,
            stylePlaceholderPoster: "background-image: url('https://d994l96tlvogv.cloudfront.net/uploads/film/poster/poster-image-coming-soon-placeholder-no-logo-500-x-740_26588.png')"
        }
    },
    methods: {
        fixFlag(flag) {
            if(flag == 'en'){
                return flag = "gb";
            } else if(flag == 'ja'){
                return flag = "jp";
            } else if(flag == 'hi'){
                return flag = "in";
            } else if(flag == 'cs'){
                return flag = "cz";
            } else if(flag == 'ko'){
                return flag = "kr";
            } else if(flag == 'sv'){
                return flag = "ch";
            } return flag
        }
    }
}
</script>


<style lang="scss" scoped>
.ms_card {
    border: 1px solid black;
    color: white;
    padding: 1rem;
    margin-bottom: 1.5rem;
    background-size: cover;
    background-position: top center;
    background-repeat: no-repeat;
    height: 22rem;
    transition: all 0.5s;
    cursor: pointer;

    ul {
        opacity: 0;
        transition: all 0.5s;
        font-size: 0.8rem;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        height: 100%;
        white-space: normal;

        .flag {
        width: 1.5rem;
        }
        .stars-container {
            display: flex;

            .star {
                color: #696969;
            }
            .star.active {
                color: #ffc400;
            }
        }
    }
}
.ms_card:hover {
    background-image: none !important;

    ul {
        opacity: 1;
    }
}
</style>
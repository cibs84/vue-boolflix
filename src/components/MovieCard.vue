<template>
    <!-- <div class="col"> -->
        <div class="ms_card">
            <ul>
                <li>{{title}}</li>
                <li>{{originalTitle}}</li>
                <li>
                    <img class="flag" :src="`https://countryflagsapi.com/png/${this.fixFlag(language)}`">
                </li>
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
    },
    data(){
        return {
            flagIsVisible: true
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
    border: 1px solid white;
    color: white;
    padding: 1rem;
    margin-bottom: 1.5rem;

    .flag {
        width: 1.5rem;
    }
}
</style>
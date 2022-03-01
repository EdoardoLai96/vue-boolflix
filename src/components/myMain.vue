<template>
<div class="container">
    <div class="movie_box">
        <myMovieCard :movie="movie" v-for="(movie, index) in moviesCatalogue" :key="'movie-'+ index" />
      
        <myTvShowCard :tvShow="tvShow" v-for="(tvShow, index) in tvShowsCatalogue" :key="'tvShow-'+ index" />
    </div>
</div>
</template>

<script>
import myMovieCard from '../components/partials/myMovieCard.vue';
import myTvShowCard from '../components/partials/myTvShowCard';
export default {
    name: "myMain",
    data(){
        return{
         info : []
        }
    },
    props: {
        moviesCatalogue: Array,
        tvShowsCatalogue: Array,
        },
    components: {
        myMovieCard,
        myTvShowCard,
    },
    computed:{
        getComputedMoviesStars(){
            return this.moviesCatalogue.map(element => {
                return Math.ceil(element.vote_average / 2)
            }); 
        },
        getComputedTvShowsStars(){
            return this.tvShowsCatalogue.map(element => {
                return Math.ceil(element.vote_average / 2)
            }); 
        },
    }
}
</script>

<style scoped lang="scss">
    .fa-star{
        color: rgb(255, 230, 0);
    }

    .container{
        background-color: rgb(31, 31, 31);
        min-height: calc(100vh - 100px);
        padding: 4rem;
        .movie_box{
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }
    }
</style>
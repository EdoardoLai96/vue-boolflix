<template>
<div class="container" id="main_container">
    <div id="input_search_box">
        <h1>Type a Movie or a Tv Show title:</h1>
        <input v-model="searchedTextMain" @keypress.enter="searchMain()" type="text" >
    </div>
    <h1 id="movies_headline">MOVIES</h1>
    <div class="movie_box">
        <myMovieCard :movie="movie" v-for="(movie, index) in moviesCatalogue" :key="'movie-'+ index" />
    </div>
    <h1 id="tv_shows_headline">TV SHOWS</h1>
    <div class="movie_box">
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
         info : [],
         searchedTextMain : ''
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
    },
    methods:{
        searchMain(){
            this.$emit("searchMovieMain", this.searchedTextMain),
            this.$emit("searchTvShowMain", this.searchedTextMain)
            if(document.getElementById("input_search_box")){
            document.getElementById("input_search_box").remove();
            document.getElementById("movies_headline").style.display = "block",
            document.getElementById("tv_shows_headline").style.display = "block"
            document.getElementById("main_container").style.display = "block"
        }

        }
    },
    Unmounted(){
            document.getElementById("movies_headline").innerHTML = "MOVIES",
            document.getElementById("tv_shows_headline").innerHTML = "TV SHOWS"

    },
}
</script>

<style scoped lang="scss">
    .fa-star{
        color: rgb(255, 230, 0);
    }
    h1{
        margin-bottom: 4rem;
        color: white;
        font-size: 3rem;
        font-family: Arial, Helvetica, sans-serif;
        text-align: center;
    }
    .container{
        background-color: rgb(31, 31, 31);
        min-height: calc(100vh - 100px);
        padding: 4rem;
        transition: 5s;
        display: flex;
        justify-content: center;
        align-items: center;
        #input_search_box{
            flex-direction: row;
            input{
               width: 100%;
                height: 50px;
                font-size: 2rem;
                outline: none;
            }
        }
        #movies_headline, #tv_shows_headline{
            display: none;
        }
        .movie_box{
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 3rem;
            justify-items: flex-start;
        }
        

    }

        .animation{
         animation-name: example;
         animation-duration: 4s;

        } 

        @keyframes example {
         from {background-color: red;}
         to {background-color: yellow;}
        }
</style>
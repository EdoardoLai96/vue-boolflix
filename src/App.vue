<template>
  <div id="app">
    <myHeader @searchMovie="getMovies" @searchTvShow="getTvShows"/>
    <myMain  :moviesCatalogue="moviesCatalogue" :tvShowsCatalogue="tvShowsCatalogue" @searchMovieMain="getMovies" @searchTvShowMain="getTvShows"/>
    
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'
  const axios = require('axios');

export default {
  
  name: 'App',
  data(){
    return{
      moviesCatalogue : [],
      moviePoster : 'https://image.tmdb.org/t/p/',
      movieVotes : [],
      tvShowsCatalogue : [],
      tvShowPoster : 'https://image.tmdb.org/t/p/',
      tvShowVotes : [],

    }
  },
  components: {
    myHeader,
    myMain,
  },
  computed:{
    getComputedStar(){
      return this.moviesCatalogue.vote_average
    }
  },
  methods:{
    getMovies(keyword){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=ec674a7dac50b060978edf782fd5605e&query='+ keyword +'')
      .then((response)=>{
        this.moviesCatalogue = response.data.results
      })
      .catch(function (error) {
        console.log(error);
      })
    },
    getTvShows(keyword){
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=ec674a7dac50b060978edf782fd5605e&query='+ keyword +'')
      .then((response)=>{
        this.tvShowsCatalogue = response.data.results
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      })
    },
},
}
</script>

<style lang="scss">
@import url('./assets/style/general.scss');
@import "~@fortawesome/fontawesome-free/css/all.css";

#app{
  height: 100%;
}
</style>

<template>
  <div id="app">
    <myHeader @searchMovie="getMovies" @searchTvShow="getTvShows"/>
    <myMain :tvShowVotes="tvShowVotes" :movieVotes="movieVotes" :moviesCatalogue="moviesCatalogue" :tvShowsCatalogue="tvShowsCatalogue"/>
    
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
  methods:{
    getMovies(keyword){
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=ec674a7dac50b060978edf782fd5605e&query='+ keyword +'')
      .then((response)=>{
        response.data.results.forEach(element => {
          this.movieVotes.push(Math.ceil(element.vote_average / 2))
        });
        this.moviesCatalogue = response.data.results
      })
      .catch(function (error) {
        console.log(error);
      })
    },
    getTvShows(keyword){
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=ec674a7dac50b060978edf782fd5605e&query='+ keyword +'')
      .then((response)=>{
         response.data.results.forEach(element => {
          this.tvShowVotes.push(Math.ceil(element.vote_average / 2))
        });
        this.tvShowsCatalogue = response.data.results
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      })
    },
},
// computed :{
//       convertedMovieVote(){
//        return this.moviesCatalogue.forEach(element => {
//           return console.log(Math.ceil(element.vote_average / 2))
          
//         });
//     }

// }
}
</script>

<style lang="scss">
@import url('./assets/style/general.scss');
</style>

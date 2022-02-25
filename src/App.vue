<template>
  <div id="app">
    <myHeader/>
    <myMain  :moviesCatalogue="moviesCatalogue"/>
    
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
      moviesCatalogue : []
    }
  },
  components: {
    myHeader,
    myMain,
  },
    methods:{
      getMovies(){
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=ec674a7dac50b060978edf782fd5605e&query=ghost')
    .then((response)=>{
      // handle success
      console.log(response.data.results);
      this.moviesCatalogue.push(response.data.results)
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .then(function () {
      // always executed
    });
      }
  },
  mounted(){
    this.getMovies()
  }
}
</script>

<style lang="scss">
@import url('./assets/style/general.scss');
</style>

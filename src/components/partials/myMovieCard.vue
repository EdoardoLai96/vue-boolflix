<template>
        <div  class="movie_card flip-card">
            <div class="flip-card-inner">
                <div class="flip-card-front">
                    <img v-if="movie.poster_path" :src="'https://image.tmdb.org/t/p/w342/'+movie.poster_path" style="width: 100%; height: 100%;">
                    <img v-else src="../../assets/download.png">
                </div>
                <div class="flip-card-back">
                <div class="card_element"> <h3 class="element_text">Titolo: </h3>  {{movie.title}}</div>
                <div class="card_element"> <h3 class="element_text">Titolo Originale: </h3>  {{movie.original_title}}</div>
                <div class="card_element"> 
                  <h3 class="element_text">Lingua: </h3>   <lang-flag :iso="movie.original_language" />
                </div>
                    Voto: <i class="fa-star" v-for="i in 5" :key="i" :class="i <= getComputedStar ? 'fa-solid' : 'fa-regular'" ></i>
                <div class="overview card_element">
                    <h3 class="element_text">Overview:</h3>
                    {{movie.overview}}
                </div>
                </div>
            </div>
        </div>

</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: "myMovieCard",
    data(){
        return{
            
        }
    },
    components:{
        LangFlag,
    },
    props: {
        "movie" : Object
        },
    methods:{

    },
    computed:{
        getComputedStar(){
            return Math.ceil(this.movie.vote_average / 2)
        }
    }


}
</script>

<style scoped lang="scss">

    *{
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif
    }

    .fa-star{
        color: rgb(255, 230, 0);
    }


          .movie_card{
               
                overflow-y: hidden;
                scrollbar-width: none;
                &::-webkit-scrollbar{
                    display: none;
                }
                    .card_element{
                        .element_text{
                            display: inline-block;
                            margin: 0.2rem 0;
                        }
                        img{
                            width: 100%;
                            height: 100%;
                            object-fit: cover;
                        }
                    }
            }

//Flip card//
.flip-card {
  background-color: transparent;
  width: calc(100% / 8);
  height: 350px;
  border: 1px solid #f1f1f1;
  color: white;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
  transform-style: preserve-3d;
}

.flip-card-front, .flip-card-back {
  position: absolute;
  z-index: 2;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
}

.flip-card-back {
  padding: 0.8rem;
  background-color :transparent;
  color: white;
  transform: rotateY(180deg);
}





</style>
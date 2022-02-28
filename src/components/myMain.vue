<template>
<div class="container">
    <div class="movie_box">
        <div v-for="(movie, index) in moviesCatalogue" :key="'movie-'+ index" class="movie_card">
        <ul>
            <li>Titolo: {{movie.title}}</li>
            <li>Titolo Originale: {{movie.original_title}}</li>
            <li>
                Lingua: <lang-flag :iso="movie.original_language" />
            </li>
                Voto:
                <font-awesome-icon icon="fa-star" v-for="(vote_in_stars, indice) in movieVotes[index]" :key="indice"/>
            <li>
                <img :src="'https://image.tmdb.org/t/p/w342/'+movie.poster_path">
            </li>
            <li class="overview">
                <p>Overview:</p>
                {{movie.overview}}
            </li>
        </ul>
        </div>
        <div v-for="(tvShow, index) in tvShowsCatalogue" :key="'tvShow-'+ index" class="movie_card">
        <ul>
            <li>Titolo: {{tvShow.name}}</li>
            <li>Titolo Originale: {{tvShow.original_name}}</li>
            <li>
                Lingua:
                <lang-flag :iso="tvShow.original_language" />
            </li>
            <li>
                Voto:
             <font-awesome-icon icon="fa-star" v-for="(vote_in_stars, indice) in tvShowVotes[index]" :key="indice"/>
            </li>
            <li>
                <img :src="'https://image.tmdb.org/t/p/w342/'+tvShow.poster_path">
            </li>
            <li class="overview">
                <p>Overview:</p>
                {{tvShow.overview}}
            </li>
        </ul>
        </div>
    </div>
</div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import { library } from '@fortawesome/fontawesome-svg-core';
import { faStar } from '@fortawesome/free-solid-svg-icons';

library.add(faStar)


export default {
    name: "myMain",
    props: {
        moviesCatalogue: Array,
        tvShowsCatalogue: Array,
        movieVotes: Array,
        tvShowVotes: Array
        },
    components: {
        LangFlag,
    }
}
</script>

<style scoped lang="scss">
    .fa-star{
        color: rgb(255, 230, 0);
    }

    .container{
        background-color: brown;
        min-height: calc(100vh - 200px);
        padding: 4rem;
        .movie_box{
            display: flex;
            flex-wrap: wrap;
            gap: 1.2rem;
            justify-content: center;
            .movie_card{
                width: calc(100% / 8);
                height: 350px;
                position: relative;
                background-color: black;
                color: white;
                padding: 0.7rem;
                overflow-y: auto;
                &:hover{
                    cursor: pointer;
                }
                &:hover img{
                    transition: 0.3s;
                    opacity: 0;
                }
                ul{
                
                list-style: none;
                    li{
                        margin: 5px 0;
                        img{
                            width: 100%;
                            height: 100%;
                            position: absolute;
                            top: 0;
                            object-fit: cover;
                            left: 0;
                        }
                    }
                }
            }
        }
    }
</style>
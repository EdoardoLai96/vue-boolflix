<template>
<div class="container">
    <div class="movie_box">
        <div v-for="(movie, index) in moviesCatalogue" :key="'movie-'+ index" class="movie_card">
        <ul>
            <li>{{movie.title}}</li>
            <li>{{movie.original_title}}</li>
            <lang-flag :iso="movie.original_language" />
            <li>{{movie.vote_average}}</li>
            <li>
                <img :src="'https://image.tmdb.org/t/p/w342/' + movie.poster_path">
            </li>
        </ul>
        </div>
        <div v-for="(tvShow, index) in tvShowsCatalogue" :key="'tvShow-'+ index" class="movie_card">
        <ul>
            <li>{{tvShow.name}}</li>
            <li>{{tvShow.original_name}}</li>
            <lang-flag :iso="tvShow.original_language" />
            <li>{{tvShow.vote_average}}</li>
        </ul>
        </div>
    </div>
</div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
 
export default {
    name: "myMain",
    props: {
        moviesCatalogue: Array,
        tvShowsCatalogue: Array,
        },
    components: {
        LangFlag
    }
}
</script>

<style scoped lang="scss">
    .container{
        background-color: brown;
        min-height: calc(100vh - 200px);
        padding: 4rem;
        .movie_box{
            display: flex;
            flex-wrap: wrap;
            .movie_card{
                width: calc(100% / 10);
             ul{
                list-style: none;
                img{
                    max-width: 100%;
                    max-height: 100%;
                }
             }
            }
        }
    }
</style>
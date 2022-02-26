<template>
<div class="container">
    <div class="movie_box">
        <div v-for="(movie, index) in moviesCatalogue[0]" :key="index" class="movie_card">
        <ul>
            <li>{{movie.title}}</li>
            <li>{{movie.original_title}}</li>
            <li>{{movie.original_language}}</li>
            <li>{{movie.vote_average}}</li>
        </ul>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: "myMain",
    props: {
        moviesCatalogue: Array
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
             }
            }
        }
    }
</style>
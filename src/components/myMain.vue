<template>
<div class="container">
    <div class="movie_box">
        <ul v-for="(movie, index) in moviesCatalogue[0]" :key="index">
            <li>{{movie.title}}</li>
            <li>{{movie.title}}</li>
            <li>{{movie.title}}</li>
            <li>{{movie.title}}</li>
        </ul>
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
            ul{
                list-style: none;
            }
        }
    }
</style>
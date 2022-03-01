<template>
  <div class="container">
          <div class=" logo_box">
           BOOLFLIX
          </div>
          <form class="search_box text-end">
            <input v-model="searchedText">
             <button type="submit" @click.prevent="search()">Search</button>
          </form>
  </div>
</template>

<script>
export default {
    name : "myHeader",
    data(){
        return{
          searchedText: ''
        }
    },
    methods:{
        search(){
            this.$emit("searchMovie", this.searchedText),
            this.$emit("searchTvShow", this.searchedText)
        }
    }
}
</script>

<style scoped lang="scss">
    .container{
        height: 100px;
        background-color: azure;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1.2rem;
        background-color: black;
        .logo_box{
            color: red;
            font-size: 2.5rem;
            font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
            img{
                height: 100%;
            }
        }
        .search_box{
            color: white;
            font-size: 2.5rem;
                font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            input{
                vertical-align: middle;
                font-size: 1rem;
                margin-right: 5px;
                outline: none;
            }
            button{
                font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
                vertical-align: middle;
                font-size: 1rem;

            }

        }
    }
</style>
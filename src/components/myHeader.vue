<template>
  <div class="container">
          <div class=" logo_box">
              <img src="../assets/netflix-logo.png" alt="">
          </div>
          <form class="search_box text-end">
             cerca film <input v-model="searchedText">
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
        height: 200px;
        background-color: azure;
        display: flex;
        justify-content: space-between;
        padding: 1.2rem;
        .logo_box{

            img{
                height: 100%;
            }
        }
    }
</style>
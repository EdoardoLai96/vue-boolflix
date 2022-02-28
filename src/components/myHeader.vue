<template>
  <div class="container">
          <div class=" logo_box">
              <img src="../assets/netflix-logo.png" alt="">
          </div>
          <form class="search_box text-end">
             cerca film <input v-model="searchedText" type="text" name="" id="">
             <button type="submit" @click.prevent="$emit('search', searchedText)">Search</button>
          </form>
  </div>
</template>

<script>
export default {
    name : "myHeader",
    data(){
        return{
            searchedText : '',
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
<template>
  <div class="container">
          <div class=" logo_box">
              <img src="../assets/netflix-logo.png" alt="">
          </div>
          <div class="col search_box text-end">
             cerca film <input type="text" name="" id="">
             <button>Search</button>
          </div>
  </div>
</template>

<script>
export default {
    name : "myHeader",
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
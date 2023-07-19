<script>
//import
import {store} from '../store.js'

   export default {
    data() {
      return{
        //dati
        store,
        flag: false
      }
    },
    methods: {
        //function
    },
    components: {
        //dichiarazione
    },
    props:{
        //utilizzo per file padre
    }
    
    
  }
</script>


<template>

    <main>
      <div class="container">
        <div class="row justify-content-center">

          <div class="my_card" v-for="(singleMovie, index) in store.movie" :key="index">
            <div>

                <div class="img_movie">
                    <img :src="`https://image.tmdb.org/t/p/w342${singleMovie.backdrop_path}`" alt="">
                </div>
              <h5>
                {{ singleMovie.title }}
              </h5>
              <h6>
                {{ singleMovie.original_title }}
              </h6>
              <div class="flag_box">
                  <img :src="`src/assets/img/${singleMovie.original_language}.png`" alt="">
              </div>
              <!-- <h6>
                {{ singleMovie.original_language }}
              </h6> -->
              <strong>
                {{ singleMovie.vote_average }}
              </strong>
            </div>
          </div>

          <div class="my_card series" v-for="(singleFilm, index) in store.serietv" :key="index">
            <div>

                <div class="img_movie">
                    <img :src="`https://image.tmdb.org/t/p/w342${singleFilm.backdrop_path}`" alt="">
                </div>
              <h5>
                {{ singleFilm.name }}
              </h5>
              <h6>
                {{ singleFilm.original_name }}
              </h6>
              
              <div class="flag_box">
                  <img :src="`src/assets/img/${singleFilm.original_language}.png`" alt="">
              </div>
              <!-- <h6>
                {{ singleFilm.original_language }}
              </h6> -->
              <strong>
                {{ singleFilm.vote_average }}
              </strong>
            </div>
          </div>

        </div>
      </div>
    </main>

</template>




<style lang="scss" scoped>
@use '../assets/scss/variables.scss' as *;

main {
    height: calc(100vh - 100px);
    background-color: bisque;
    overflow-y: auto;
}

.my_card {
    width: calc(100% / 6);
    height: 250px;
    text-align: center;
    margin: 10px 10px;
    padding: 10px 5px;
    background-color: chocolate;

    .img_movie{

        img {
            width: 100%;
            object-fit: cover;
        }
    }

    .flag_box{
        width: 15px;
        height: 10px;
        margin-bottom: 20px;

        img{
            width: 100%;
        }
    }
}

.series {
    background-color: purple;
}
</style>
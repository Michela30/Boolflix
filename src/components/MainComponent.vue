<script>
//import
import {store} from '../store.js'

   export default {
    data() {
      return{
        //dati
        store,
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
              <h4>
                {{ singleMovie.title }}
              </h4>
              <h6>
                {{ singleMovie.original_title }}
              </h6>
              <h6>
                {{ singleMovie.original_language }}
              </h6>
              <strong>
                {{ singleMovie.vote_average }}
              </strong>
            </div>
          </div>

          <div class="my_card_series" v-for="(singleFilm, index) in store.serietv" :key="index">
            <div>
              <h4>
                {{ singleFilm.name }}
              </h4>
              <h6>
                {{ singleFilm.original_name }}
              </h6>
              <h6>
                {{ singleFilm.original_language }}
              </h6>
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

main{
 
  background-color: bisque;
}

.my_card{
  width: 200px;
  height: 250px;
  text-align: center;
  margin: 50px 10px;
  padding: 10px 5px;
  background-color: chocolate;
}

.my_card_series{
  width: 200px;
  height: 250px;
  text-align: center;
  margin: 50px 10px;
  padding: 10px 5px;
  background-color: purple;
}
</style>
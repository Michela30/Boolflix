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
              <h2>
                {{ singleMovie.title }}
              </h2>
              <h4>
                {{ singleMovie.original_title }}
              </h4>
              <h6>
                {{ singleMovie.original_language }}
              </h6>
              <strong>
                {{ singleMovie.vote_average }}
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
  height: 200px;
  text-align: center;
  margin: 50px 10px;
  padding: 10px;
  background-color: chocolate;
}
</style>
<script>
//import
import {store} from '../store.js'
import SingleMovieSeries from '../components/SingleMovieSeries.vue'

   export default {
    data() {
      return{
        //dati
        store,

      }
    },
    methods: {
        //function
        getVote(value){
            
            const finalVote = Math.floor(value / 2 );
        
            console.log(finalVote)
            return finalVote
        },
    },
    computed:{

    },
    components: {
        //dichiarazione
        SingleMovieSeries,
    },
    props:{
        //utilizzo per file padre
    }
    
    
  }
</script>


<template>

    <main>
      
          <h3 class="ms-2">
              Movie
          </h3>

        <div class="d-flex">
        <!-- movie-->
            <div class="my_card mb-5" v-for="(singleMovie, index) in store.movie" :key="index">
            <SingleMovieSeries :elementData="singleMovie"/>
            </div>

        </div>
        
        <h3 class="mt-5 m-2">
            Serie Tv
        </h3>
        <!-- serie tv -->

        <div class="d-flex">

            <div class="my_card series" v-for="(singleSeries, index) in store.serietv" :key="index">
                <SingleMovieSeries :elementData="singleSeries"/>
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
    padding: 20px 30px;
}

.my_card {
    width: 200px;
    height: 300px;
    text-align: center;
    margin: 10px 10px;
    flex-shrink: 0;

}

</style>
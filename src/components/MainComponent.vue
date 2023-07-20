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
      
        <h3 class="text-white ms-2">
            Movie
        </h3>

        <div class="d-flex card-row">
        <!-- movie-->
            <div v-if="store.movie.length > 0" class="d-flex">
                <div class="my_card mb-5" v-for="(singleMovie, index) in store.movie" :key="index">
                <SingleMovieSeries :elementData="singleMovie"/>
                </div>

            </div>
            <div v-else>
                <h3 class="overflow-y-hidden">
                   Non ci sono risultati 
                </h3>
            </div>

        </div>
        
        <h3 class="text-white mt-5 m-2">
            Serie Tv
        </h3>
        <!-- serie tv -->

        <div class="d-flex card-row">

            <div v-if="store.serietv.length > 0" class="d-flex">

                <div class="my_card series" v-for="(singleSeries, index) in store.serietv" :key="index">
                    <SingleMovieSeries :elementData="singleSeries"/>
                </div>
            </div>

            <div v-else>
                <h3 class="overflow-y-hidden">
                   Non ci sono risultati 
                </h3>
            </div>
        </div>
    
      
    </main>

</template>




<style lang="scss" scoped>
@use '../assets/scss/variables.scss' as *;

main {
    background-color: black;
    padding: 20px 30px;
}
.card-row{
    overflow-x: auto;
}
.my_card {
    width: 200px;
    height: 300px;
    text-align: center;
    margin: 10px 10px;
    flex-shrink: 0;
    
}

</style>
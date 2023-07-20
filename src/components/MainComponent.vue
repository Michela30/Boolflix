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
      <div class="container">
        <div class="row justify-content-center">

        <!-- movie-->

        <h1>
            Movie
        </h1>
            <div class="my_card" v-for="(singleMovie, index) in store.movie" :key="index">
            <SingleMovieSeries :elementData="singleMovie"/>
            </div>

        <!-- serie tv -->
        
        <h1 class="mt-5">
            Serie Tv
        </h1>

            <div class="my_card series" v-for="(singleSeries, index) in store.serietv" :key="index">
                <SingleMovieSeries :elementData="singleSeries"/>
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
    height: 300px;
    text-align: center;
    margin: 10px 10px;
    padding: 10px 5px;
    background-color: chocolate;

   
}

.series {
    background-color: purple;
}
</style>
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
        
        <h3 id="popular" class="text-white mt-5 m-2">
            Popular Movie
        </h3>

        <div class="d-flex card-row">
            <!-- popular movie-->
            
            <div class="my_card mb-5" v-for="(singlePopularMovie, index) in store.popularMovie" :key="index">
                <SingleMovieSeries :elementData="singlePopularMovie"/>
            </div> 
        </div>
        


        <h3 id="favourite" class="text-white mt-5 m-2">
            Your favourite
        </h3>

        <div class="d-flex card-row">
            <!-- favourite movie-->
            
            <div class="my_card mb-5" v-for="(singleFavourite, index) in store.myFavourite" :key="index">
                <SingleMovieSeries :elementData="singleFavourite"/>
            </div> 
        </div>




        <h3 class="text-white mt-5 ms-2" id="movie">
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
                <h3 class="overflow-y-hidden pt-2 ms-2">
                   Non ci sono risultati 
                </h3>
            </div>

        </div>
        
        <h3 class="text-white mt-5 ms-2" id="series">
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
                <h3 class="overflow-y-hidden pt-2 ms-2">
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
    background-color: transparent;
}

::-webkit-scrollbar {
    width: 3px;
}
::-webkit-scrollbar-track {
    box-shadow: inset 0 0 5px grey;
    border-radius: 10px;
}

::-webkit-scrollbar-thumb {
    background-color: grey;
    border-radius: 10px;
}
.my_card {
    width: 200px;
    height: 250px;
    text-align: center;
    margin: 10px 10px;
    flex-shrink: 0;
    
}

.img_movie {
        height: 250px;
        position: relative;
        
        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

.description {
    display: none;
    width: 200px;
    background-color: rgba(0,0,0,0.8);
    padding: 15px;
    color: white;
    overflow-y: auto;
    font-size: 1em;

    
    .flag_box {
        width: 15px;
        height: 10px;
        margin-bottom: 20px;
        margin-left: calc(150px / 2);

        img {
            width: 100%;
        }
    }

    .fa-star{
        padding-top: 10px;
        color: gold;
    }

    .overview{
        font-size: 0.8em;
    }
}

.img_movie:hover .description {
    display: block;
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}

</style>
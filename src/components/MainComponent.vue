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
        flag(){
            if(this.store.popularMovie.original_language == 'en'){
                return 'https://flagicons.lipis.dev/flags/4x3/gb.svg'
            }
            else if(this.store.popularMovie.original_language == 'it'){
                return 'https://flagicons.lipis.dev/flags/4x3/it.svg'
            }
            else if(this.store.popularMovie.original_language == 'fr'){
                return 'https://flagicons.lipis.dev/flags/4x3/fr.svg'
            }
            else if(this.store.popularMovie.original_language == 'sp'){
                return 'https://flagicons.lipis.dev/flags/4x3/sp.svg'
            }
            else if(this.store.popularMovie.original_language == 'de'){
                return 'https://flagicons.lipis.dev/flags/4x3/de.svg'
            }
            else{
                return 'https://flagicons.lipis.dev/flags/4x3/xx.svg'
            }
        }
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
        
        <h3 class="text-white mt-5 m-2">
            Popular Movie
        </h3>
    <div class="d-flex card-row">
        <!-- popular movie-->
            
        <div class="my_card mb-5" v-for="(singlePopularMovie, index) in store.popularMovie" :key="index">
        <div class="img_movie">
            <img v-if="singlePopularMovie.backdrop_path == null" src="../assets/img/posternotfound.png" alt="">

            <img v-else :src="`https://image.tmdb.org/t/p/original${singlePopularMovie.backdrop_path}`" alt="" class="img-fluid">
            
            <div class="description">

                <p>
                    <span>
                        Titolo: 
                    </span>
                    {{ singlePopularMovie.title }}
                </p>

                <p>
                    <span>
                        Titolo originale:
                    </span>
                {{ singlePopularMovie.original_title}}
                </p>

                <span>
                    Voto:
                    <span>
                        {{ getVote(singlePopularMovie.vote_average) }}
                    </span>

                    <!-- <i v-for="num in getVote(singlePopularMovie.vote_average)" :key="num" class="fa-solid fa-star"></i>
                    <i  v-for="num in (5 - getVote(singlePopularMovie.vote_average))" :key="num" class="fa-regular fa-star"></i> -->
                </span>
                
                <div class="flag_box mt-1">
                    <img :src="flag()" alt="">
                </div>

                <p class="overview">
                    {{ singlePopularMovie.overview }}
                </p>
            
            </div>

        </div>
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
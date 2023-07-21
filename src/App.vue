<script>
//import
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';
import StartComponent from './components/StartComponent.vue'

import {store} from './store.js'

import axios from 'axios';

   export default {
    data() {
      return{
        store,
        isLoad: false
      }
    },
    components: {
      HeaderComponent,
      MainComponent,
      FooterComponent,
      StartComponent
    },
    methods: {
      getMovie(){
          axios.get('https://api.themoviedb.org/3/search/movie?api_key=1ca56690c738fe07273dfdadfc643ca2', {
                    params: {
                        query: this.store.searchBar
                       
                    }
                })
        .then(response => {
          this.store.movie = response.data.results;

        })
      },

      getSeries(){
          axios.get('https://api.themoviedb.org/3/search/tv?api_key=1ca56690c738fe07273dfdadfc643ca2', {
                    params: {
                        query: this.store.searchBar
                       
                    }
                })
        .then(response => {
          this.store.serietv = response.data.results;
        })
      },

      getPopularMovie(){
          axios.get('https://api.themoviedb.org/3/movie/popular?api_key=1ca56690c738fe07273dfdadfc643ca2', {
                    params: {
                      page: 2,
                    }
                })
        .then(response => {
          this.store.popularMovie = response.data.results;
        })
      },

      getFavourite(){
          axios.get('https://api.themoviedb.org/3/movie/popular?api_key=1ca56690c738fe07273dfdadfc643ca2', {
                    params: {
                      page: 3,
                    }
                })
        .then(response => {
          this.store.myFavourite = response.data.results;
        })
      },

      getGenres(){
        axios.get('https://api.themoviedb.org/3/genre/movie/list?api_key=1ca56690c738fe07273dfdadfc643ca2' )

        .then(response => {
          this.store.genres = response.data.genres;
        })
      },

      getDiscoveredMovie(genreId){
        axios.get('https://api.themoviedb.org/3/discover/movie?api_key=1ca56690c738fe07273dfdadfc643ca2', {
          params: {
            with_genres: genreId
          }
        })

        .then(response => {
          this.store.discoveredMovie = response.data.results;
        })
      },

      searchMovie(){
      
        this.getMovie();
        this.getSeries();
        
      },

      searchGenres(ev, selectedGenreId){

        this.getDiscoveredMovie(selectedGenreId)
        this.getMovie()
       
      },
    },
    created(){
      this.getMovie();
      this.getSeries();
      this.getPopularMovie();
      this.getFavourite();
      this.getGenres();
      this.getDiscoveredMovie()
    },
    mounted(){

      setTimeout(() => {
        this.isLoad = true;
      }, 2500);
    
    },
  }
</script>



<template>
  <StartComponent v-if="!isLoad" />

  <div v-else>
    
    <HeaderComponent @search="searchMovie" @searchGenres="searchGenres"/>

    <MainComponent/>

    <FooterComponent/>

  </div>
</template>




<style lang="scss">
@use 'assets/scss/main.scss';


</style>

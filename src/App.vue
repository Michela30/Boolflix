<script>
//import
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';

import {store} from './store.js'

import axios from 'axios';

   export default {
    data() {
      return{
        store,
      }
    },
    components: {
      HeaderComponent,
      MainComponent,
      FooterComponent
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

      searchMovie(){
        this.getMovie();
        this.getSeries();
        console.log('azione cerca film')
      },
      
    },
    created(){
      this.getMovie();
      this.getSeries();

    }
  }
</script>



<template>
  <div>
    <HeaderComponent @search="searchMovie()"/>

    <MainComponent/>

    <FooterComponent/>

  </div>
</template>




<style lang="scss">
@use 'assets/scss/main.scss';




</style>

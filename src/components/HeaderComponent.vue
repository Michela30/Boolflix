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
    
    <header>
       <div class="search_bar">
            <div class="container">
                <div class="row">
                    <div class="col-6">
                        logo
                    </div>

                    <div class="col-6">
                        <form action="" @submit.prevent="$emit('search')">

                            <input v-model="store.searchBar" type="text" name="" id="" placeholder="Ricerca">
    
                            <button type="submit">
                                Invia
                            </button>

                        </form>
                    </div>
                </div>
            </div>
       </div>
    </header>

</template>



<style lang="scss" scoped>
@use '../assets/scss/variables.scss' as *;

header{
    height: 50px;
    background-color: black;
    color: white;
}

</style>
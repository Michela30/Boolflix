<script>
//import

   export default {
    data() {
      return{
        //dati
      }
    },
    methods: {
        //function
    },
    computed: {
        vote(){
            
            const finalVote = Math.ceil(this.elementData.vote_average / 2 );
            return finalVote
        },

        flag(){
            if(this.elementData.original_language == 'en'){
                return 'https://flagicons.lipis.dev/flags/4x3/gb.svg'
            }
            else if(this.elementData.original_language == 'it'){
                return 'https://flagicons.lipis.dev/flags/4x3/it.svg'
            }
            else if(this.elementData.original_language == 'fr'){
                return 'https://flagicons.lipis.dev/flags/4x3/fr.svg'
            }
            else if(this.elementData.original_language == 'sp'){
                return 'https://flagicons.lipis.dev/flags/4x3/sp.svg'
            }
            else if(this.elementData.original_language == 'de'){
                return 'https://flagicons.lipis.dev/flags/4x3/de.svg'
            }
            else{
                return 'https://flagicons.lipis.dev/flags/4x3/xx.svg'
            }
        }
        
    },
    props:{
        elementData: {
            type: Object,
            default: null
        }
    }
    
  }
</script>


<template>
    
    <div>

        <div class="img_movie">
            <img v-if="elementData.backdrop_path == null" src="../assets/img/posternotfound.png" alt="">

            <img v-else :src="`https://image.tmdb.org/t/p/original${elementData.backdrop_path}`" alt="">
        </div>
            <h5>
            {{ elementData.title ?? elementData.name }}
            </h5>
            <h6>
            {{ elementData.original_title ?? elementData.original_name }}
            </h6>

            <div class="flag_box">
            <img :src="flag" alt="">
            </div>
        
            <strong>
                {{ vote }}
                <i v-for="num in vote" :key="num" class="fa-solid fa-star"></i>
                <i  v-for="num in (5 - vote)" :key="num" class="fa-regular fa-star"></i>
            </strong>

</div>

</template>



<style lang="scss" scoped>
@use '../assets/scss/variables.scss' as *;
.img_movie {
        height: 250px;
        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    }

    .flag_box {
        width: 15px;
        height: 10px;
        margin-bottom: 20px;

        img {
            width: 100%;
        }
    }

    .fa-star{
        color: gold;
    }
</style>
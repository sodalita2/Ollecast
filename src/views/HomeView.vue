<script setup>
import { ref } from 'vue';
import { RouterLink, RouterView } from 'vue-router';
import axios from 'axios';
import $ from 'jquery';
import ClipLoader from "vue-spinner/src/ClipLoader.vue"


const popular_banner = ref('');


axios.get('https://api.themoviedb.org/3/movie/popular?api_key=ae09440b9c0c8580e7c47dd2d54bbd7e&language=pt-BR&append_to_response=images', {
    params: {
        movie_id: 5,
    },
    headers: { 'Content-Type': 'json' }
}).then( (response) => {
    
    popular_banner.value = response.data.results[0].backdrop_path;

});


</script>

<template>

    <!-- Wrapper -->
    <div class="w-full h-auto flex flex-col">
        <!-- Popular Banner -->
        <div v-if="popular_banner == ''" class="w-full h-full flex justify-center items-center">
            <clip-loader color="#FFA500" size="150px"></clip-loader>
        </div>
        <div v-else class="w-full h-[700px] flex flex-col relative bg-cover bg-no-repeat" v-bind:style="{'background-image': `url(https://image.tmdb.org/t/p/original/${popular_banner})`}">
        </div>
    </div>
  
</template>

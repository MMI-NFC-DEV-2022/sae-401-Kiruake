<script setup lang="ts">

import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
defineProps <Database["public"]["Tables"]["films"]["Row"] & {celebrites:Tables<'celebrites'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} & {supports:Tables<'supports'>[]} & {film_support:Tables<'film_support'>[]} >()

 
</script>


<template>
 
 <div>
    <img class="object-cover w-full h-[500px] " :src="banniere ?? undefined"/>

    <div class="flex pl-2 pb-2 absolute top-20">
        <div v-for="n in note??0" class="text-white">
            <svg class="w-5 h-5 fill-current text-yellow-500" viewBox="0 0 24 24">
                <path d="M12 2L14.47 8.53L21 9.35L16.24 13.77L17.47 20.07L12 17.77L6.53 20.07L7.76 13.77L3 9.35L9.53 8.53L12 2Z" />
            </svg>
        </div>
        <div v-for="n in (5-(note??0))" class="text-white ">
            <svg class="w-5 h-5 fill-current text-white" viewBox="0 0 24 24">
                <path d="M12 2L14.47 8.53L21 9.35L16.24 13.77L17.47 20.07L12 17.77L6.53 20.07L7.76 13.77L3 9.35L9.53 8.53L12 2Z" />
            </svg>
        </div>
        </div>
    </div>


    <section class="flex-col flex  lg:flex-row">

        <div class="text-gray-300 lg:ml-10 mt-10 lg:w-3/6 w-6/6 ml-5 mr-5 lg:mr-0 lg:ml-10 tracking-wide">

            <h2 class="lg:text-3xl text-2xl text-center lg:text-start uppercase ">{{ titre }} ({{ date_de_sortie }})</h2>
            <p class="mt-10 text-justify">{{ synopsis }}</p>

        <div>

            <div class="text-gray-300 border-b pb-3 mt-10 ">
                <h2>Durée : {{ duree }}</h2>
            </div>

            <div class="text-gray-300 border-b pb-3 pt-3 flex gap-2">
                <h2 v-for="(unGenre, index) in genres" :key="unGenre.id">
                    Genre : {{ unGenre.libelle }}
                    <span v-if="index !== genres.length - 1">,</span>
                </h2>
            </div>

            <div class="text-gray-300 border-b pb-3 pt-3">
                <div v-for="uneSaga in sagas">
                <RouterLink :to="{name:'/sagas/[id]', params: {id:uneSaga.id}}">
                    <p class="underline text-yellow-500" v-for="uneSaga in sagas">Saga : {{ uneSaga.libelle}} </p>
                </RouterLink>
                </div>
            </div>

        </div>

        </div>

        <div class="lg:w-3/6 w-6/6 ">
        <h2 class="text-gray-300 flex justify-center text-2xl mt-20 mb-10 tracking-wide">Où streamer ce film ?</h2>  
        
        <div class="flex flex-col gap-8">
            <div v-for="unePlateforme in plateformes" :key="unePlateforme.id" >
                <RouterLink :to="{name:'/plateformes/[id]', params: {id:unePlateforme.id}}">
                <div class="flex m-auto w-[230px] items-center gap-10 border border pl-5 py-2 rounded w-1/6">
                <img class="w-10 rounded-full" :src="unePlateforme.image ?? undefined" />
                <p class="text-xl text-gray-300">{{ unePlateforme.nom }}</p>
                    </div>
                </RouterLink>
            </div>
        </div>

        </div>

        

    </section>

         
<h1 class="lg:text-3xl text-xl text-center lg:text-start text-gray-300 lg:ml-10 ml-0 mt-20 mb-16 uppercase">
    Casting du film
    <span class="bg-yellow-500 h-1 lg:w-[70%] w-[50%] m-auto mt-4 lg:mt-0 lg:ml-8 mb-2 lg:inline-block block"></span>
</h1>

       
    <div class="flex lg:flex-row flex-col flex-wrap lg:gap-20 gap-10 lg:ml-10 mt-10">
    <div v-for="uneCelebrite in celebrites" :key="uneCelebrite.id" class="flex flex-col items-center">
        <RouterLink :to="{ name: '/celebrites/[id]', params: { id: uneCelebrite.id } }">
            <img class="w-40 h-40 object-cover rounded-full" :src="uneCelebrite.image ?? undefined" alt="Photo de {{ uneCelebrite.nom }}" />
            <p class="text-gray-300 text-xl text-center pt-4">{{ uneCelebrite.nom }}</p>
        </RouterLink>
    </div>
</div>

    
<h1 class="lg:text-3xl text-center lg:text-start text-xl text-gray-300 lg:ml-10 ml-0 mt-20 mb-16 uppercase">
    Supports disponible pour {{ titre }}
    <span class="bg-yellow-500 h-1 lg:w-[25%] w-[50%] lg:ml-8 mb-2 m-auto mt-4 lg:mt-0 lg:inline-block block"></span>
</h1>



   
       
        <ul class="ml-8 flex gap-20 justify-start flex-wrap">
            <div v-for="unSupport in supports" :key="unSupport.id">
        <li>
           
                <img class="w-40 h-40 object-cover rounded-full" :src="unSupport.image ?? undefined" alt="Photo de {{ unSupport.nom }}" />
        
        </li>

           <li>
                <p class="text-gray-300 text-xl text-center pt-4">{{ unSupport.type }}</p>
            </li>
        </div>
        </ul>

    
    <ul  class="flex ml-20 justify-start gap-44 flex-wrap">
    
        <div v-for="unFilmSupport in film_support">

        <li ><p class="text-gray-300 text-xl text-center pt-4">{{ unFilmSupport.prix }}€</p></li>
        <a :href="unFilmSupport.lien ?? ''" target="_blank">
        <li><button class="bg-yellow-500 p-1 mt-2 rounded ">Acheter</button></li>
        </a>
    </div>
        
    
    </ul>






        
    
    </template>

    <style>





</style>



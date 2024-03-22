<script setup lang="ts">

import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
const route = useRoute('/sagas/[id]');
defineProps <Database["public"]["Tables"]["sagas"]["Row"] & {films:Tables<'films'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} >()

 
</script>


<template>
 
   

       <h1 class="text-3xl text-gray-300 mt-20 ml-10">Voici toute la saga {{libelle }}
            <span class="bg-yellow-500 h-1 w-[60%] ml-8 mb-2 inline-block"></span>
        </h1>
     

    

        <div  v-for="unFilm in films">
            <RouterLink :to="{name:'/films/[id]', params: { id: unFilm.id }}">

    <div class="m-auto mt-20 bg-gray-300 w-[60%] rounded-sm flex flex-wrap shadow-lg hover:shadow-2xl hover:scale-105 transition-transform transition-shadow duration-300 ease-in-out">

     <img :src="unFilm.affiche ?? undefined" class="h-auto rounded-t-sm"/>


<div class="flex flex-col">

     <div class="text-slate-700 p-2">
         <h3 class="text-l font-semibold">{{ unFilm.titre }}</h3>
     </div>
    
     <div class="flex pl-2 pb-2">

         <div v-for="n in unFilm.note??0" class="text-white">
               <svg class="w-5 h-5 fill-current text-yellow-500" viewBox="0 0 24 24">
                  <path d="M12 2L14.47 8.53L21 9.35L16.24 13.77L17.47 20.07L12 17.77L6.53 20.07L7.76 13.77L3 9.35L9.53 8.53L12 2Z" />
               </svg>
         </div>
         
         <div v-for="n in (5-(unFilm.note??0))" class="text-white ">
               <svg class="w-5 h-5 fill-current text-white" viewBox="0 0 24 24">
                  <path d="M12 2L14.47 8.53L21 9.35L16.24 13.77L17.47 20.07L12 17.77L6.53 20.07L7.76 13.77L3 9.35L9.53 8.53L12 2Z" />
               </svg>
         </div>

     </div>

   </div>

 </div>


</RouterLink>
</div>



    
       
    </template>
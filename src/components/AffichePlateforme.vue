<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { supabase } from '@/supabase';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["plateformes"]["Row"] & {films:Tables<'films'>}  >()


</script>   

<template>

<div class="flex lg:flex-row flex-col items-center">

<img class="w-60 h-60 mt-10 lg:ml-10  object-cover rounded-full" :src="image ?? undefined"/>

<div>
 <h1 class="lg:ml-20 mt-10 text-center lg:text-start text-4xl text-gray-300">{{nom }}</h1>
 <p class="lg:ml-20 ml-5 mr-5 lg:mr-10 mt-10 text-center lg:text-start text-gray-300 leading-1">{{ description }}</p>
</div>


</div>

<h1 class="lg:text-3xl text-xl text-center lg:text-start text-gray-300 lg:ml-10 ml-0 mt-20 lg:mt-28 mb-16 uppercase">
    Tout les films disponible sur {{nom}}
    <span class="bg-yellow-500 h-1 lg:w-[50%] w-[50%] m-auto mt-4 lg:mt-0 lg:ml-8 mb-2 lg:inline-block block"></span>
</h1>


<div class="flex flex-col lg:flex-row ">
        <div v-for="unFilm in films">
            <RouterLink :to="{name:'/films/[id]', params: { id: unFilm.id }}">
    
<div class="m-auto mt-20 bg-gray-300 w-[60%] rounded-sm flex flex-wrap shadow-lg hover:shadow-2xl hover:scale-105 transition-transform transition-shadow duration-300 ease-in-out">

     <img :src="unFilm.affiche ?? undefined" class="max-h-96 w-[300px] lg:w-[380px] rounded-t-sm"/>


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

</div>
   
</template>
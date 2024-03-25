<script setup lang="ts">

import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
const route = useRoute('/celebrites/[id]');
defineProps <Database["public"]["Tables"]["celebrites"]["Row"] & {films:Tables<'films'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} >()

 
</script>


<template>
 

 <div class="flex lg:flex-row flex-col items-center">

       <img class="w-60 h-60 mt-10 lg:ml-10  object-cover rounded-full" :src="image ?? undefined"/>

       <div>
        <h1 class="lg:ml-20 mt-10 text-center lg:text-start text-4xl text-gray-300">{{prenom }} {{nom }}</h1>
        <p class="lg:ml-20 ml-5 mr-5 lg:mr-0 mt-10 text-center lg:text-start text-gray-300 leading-1">{{ biographie }}</p>
      </div>


  </div>

  <div class="lg:w-2/5 w-4/5 lg:ml-[360px] m-auto mt-10 lg:mt-0 ">
      <div class="text-gray-300 border-b pb-3 pt-3">
          <p>date de naisance :{{date_de_naissance }}</p>
      </div>

      <div class="text-gray-300 border-b pb-3 pt-3">
            <p>nombre de films:{{nb_films }}</p>
      </div>
  </div>


  <h1 class="lg:text-3xl text-xl text-center lg:text-start text-gray-300 lg:ml-10 mt-20 mb-16 uppercase">
    Voici les films dans lesquels {{prenom }} {{nom }} a joué
    <span class="bg-yellow-500 h-1 lg:w-[30%] w-[50%] lg:ml-8 mb-2 m-auto mt-4 lg:mt-0 lg:inline-block block"></span>
</h1>

      <div class="lg:flex flex-col lg:flex-row lg:ml-20 m-auto gap-20">
        <div v-for="unFilm in films" :key="unFilm.id" class="flex justify-center lg:justify-start m-auto lg:m-0 mb-20 ">
          <RouterLink :to="{ name: '/films/[id]', params: { id: unFilm.id } }">
            <img class="w-48 items-center" :src="unFilm.affiche ?? undefined" />
            <p class="text-gray-300 mt-5 ">{{ unFilm.titre }}</p>
          </RouterLink>
        </div>
      </div>


    
       
    </template>
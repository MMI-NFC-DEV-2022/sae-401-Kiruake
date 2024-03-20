<script setup lang="ts">

import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
defineProps <Database["public"]["Tables"]["films"]["Row"] & {celebrites:Tables<'celebrites'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} >()

 
</script>


<template>
 
       <img class="object-cover w-full h-[300px]" :src="affiche ?? undefined"/>

       
       <h2 class="text-3xl text-gray-300 ml-10 mt-10">{{ titre }}</h2>


       <li>Synopsis : {{ synopsis }}</li>
       <li>Durée : {{duree }}h</li>
       
       <p v-for="unGenre in genres">Genre :{{ unGenre.libelle }}</p>


       
       <li v-for="uneCelebrite in celebrites">
        <RouterLink :to="{name:'/celebrites/[id]', params: {id:uneCelebrite.id}}">
       <p>Casting : {{ uneCelebrite.nom}}</p>
       <img  class="w-72" :src="uneCelebrite.image ?? undefined"/>
        </RouterLink>
        </li>
    


         <p v-for="uneSaga in sagas">Saga : {{ uneSaga.libelle}}</p>
         <img  class="w-72" v-for="unePlateforme in plateformes" :src="unePlateforme.image ?? undefined"/>
         <p v-for="unePlateforme in plateformes">Platefromes : {{ unePlateforme.nom}}</p>
       <li>Date de sortie :{{ date_de_sortie}}</li>

    
       
    </template>
<script setup lang="ts">

import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
const route = useRoute('/sagas/[id]');
defineProps <Database["public"]["Tables"]["sagas"]["Row"] & {films:Tables<'films'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} >()

 
</script>


<template>
 
   

       <p>Voici la sage {{libelle }} complète</p>
     

       <li v-for="unFilm in films">
        <RouterLink :to="{name:'/films/[id]', params: {id:unFilm.id}}">
        <p v-for="unFilm in films">{{ unFilm.titre}}</p>
       <img  class="w-72" :src="unFilm.affiche ?? undefined"/>
        </RouterLink>
        </li>


    
       
    </template>
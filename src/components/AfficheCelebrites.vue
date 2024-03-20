<script setup lang="ts">

import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
const route = useRoute('/celebrites/[id]');
defineProps <Database["public"]["Tables"]["celebrites"]["Row"] & {films:Tables<'films'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} >()

 
</script>


<template>
 
       <img class="object-cover w-full h-[300px]" :src="image ?? undefined"/>

       <li>{{nom }}</li>
       <li>{{date_de_naissance }}h</li>
         <li>{{prenom }}</li>
            <li>{{nb_films }}</li>

       <li v-for="unFilm in films">
        <RouterLink :to="{name:'/films/[id]', params: {id:unFilm.id}}">
       <img  class="w-72" :src="unFilm.affiche ?? undefined"/>
        </RouterLink>
        </li>


    
       
    </template>
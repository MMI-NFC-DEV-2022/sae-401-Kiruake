<script setup lang="ts">
import { supabase } from '@/supabase';
import type { Database, Tables } from '@/supabase-types';
import AfficheFilm from '@/components/AfficheFilm.vue';

let { data: data, error } = await supabase
    .from('films')
    .select(`
      *,
      celebrites(*),
      genres(*),
      sagas(*)
    `);

if (error) {
      console.error("erreur rquete films avec celebrite", error);
    }
console.log(data);


const tableauFilm = data ?? [];

</script>

<template>

<h1 class="lg:text-3xl text-xl text-gray-300 lg:ml-10 text-center lg:text-start mt-20 mb-4 uppercase">
    Notre catalogue de films
    <span class="bg-yellow-500 h-1 w-[50%] lg:ml-8 m-auto mt-4 lg:mt-0 mb-2 lg:inline-block block"></span>
</h1>

    <div class="grid lg:grid-cols-3 grid-cols-1">
        <AfficheFilm v-for="film in tableauFilm" v-bind="film"/>
    </div>
</template>
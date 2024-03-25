<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
import AfficheCelebrites from '@/components/AfficheCelebrites.vue';
import AfficheSaga from '@/components/AfficheSaga.vue';
const route = useRoute('/sagas/[id]');
defineProps <Database["public"]["Tables"]["sagas"]["Row"] & {films:Tables<'films'>[]} & {genres:Tables<'genres'>[]} & {sagas:Tables<'sagas'>[]} & {plateformes:Tables<'plateformes'>[]} >()

let { data: saga, error } = await supabase
    .from('sagas')
    .select(`
      *,
      films(*)
    `)
    .eq('id', route.params.id)
    .single();

    console.log(saga);

</script>

<template>


<h1 class="text-3xl text-center lg:text-start text-gray-300 mt-20 lg:ml-10">Voici toute la saga {{libelle }}
            <span class="bg-yellow-500 h-1 lg:w-[60%] w-[50%] mt-4 lg:mt-0 m-auto lg:ml-8 mb-2 lg:inline-block block"></span>
        </h1>

    <div >
        <AfficheSaga v-bind="saga" />
    </div>
</template>
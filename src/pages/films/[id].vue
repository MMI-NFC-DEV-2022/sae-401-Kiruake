<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
defineProps <Database["public"]["Tables"]["films"]["Row"] & {celebrites:Tables<'celebrites'>} & {genres:Tables<'genres'>} & {sagas:Tables<'sagas'>} & {plateformes:Tables<'plateformes'>} & {supports:Tables<'supports'>} & {film_support:Tables<'film_support'>[]}   >()
import AfficheSingle from '@/components/AfficheSingle.vue';
const route = useRoute('/films/[id]');

let { data: film, error } = await supabase
    .from('films')
    .select(`
      *,
      celebrites(*),
      genres(*),
      sagas(*), 
      plateformes(*),
      supports(*),
        film_support(*)
    `)
    .eq('id', route.params.id)
    .single();


</script>

<template>
    <div>
        <AfficheSingle v-bind="film" />
    </div>
</template>
<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
defineProps <Database["public"]["Tables"]["plateformes"]["Row"] &  {films:Tables<'films'>} >()
import AffichePlateforme from '@/components/AffichePlateforme.vue';
const route = useRoute('/plateformes/[id]');

let { data: plateforme, error } = await supabase
    .from('plateformes')
    .select(`
      *,
      films(*)
    `)
    .eq('id', route.params.id)
    .single();


</script>

<template>
    <div>
        <AffichePlateforme v-bind="plateforme" />
    </div>
</template>
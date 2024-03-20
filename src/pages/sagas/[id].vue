<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
defineProps <Database["public"]["Tables"]["films"]["Row"] & {celebrites:Tables<'celebrites'>} & {genres:Tables<'genres'>} & {sagas:Tables<'sagas'>} & {plateformes:Tables<'plateformes'>}   >()
import AfficheCelebrites from '@/components/AfficheCelebrites.vue';
import AfficheSaga from '@/components/AfficheSaga.vue';
const route = useRoute('/sagas/[id]');

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
    <div>
        <AfficheSaga v-bind="saga" />
    </div>
</template>
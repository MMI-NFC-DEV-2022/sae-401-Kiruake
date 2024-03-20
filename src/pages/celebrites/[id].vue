<script setup lang="ts">
import { useRoute } from 'vue-router/auto';
import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
import { supabase } from '@/supabase';
defineProps <Database["public"]["Tables"]["films"]["Row"] & {celebrites:Tables<'celebrites'>} & {genres:Tables<'genres'>} & {sagas:Tables<'sagas'>} & {plateformes:Tables<'plateformes'>}   >()
import AfficheCelebrites from '@/components/AfficheCelebrites.vue';
const route = useRoute('/celebrites/[id]');

let { data: celebrite, error } = await supabase
    .from('celebrites')
    .select(`
      *,
      films(*)
    `)
    .eq('id', route.params.id)
    .single();

    console.log(celebrite);

</script>

<template>
    <div>
        <AfficheCelebrites v-bind="celebrite" />
    </div>
</template>
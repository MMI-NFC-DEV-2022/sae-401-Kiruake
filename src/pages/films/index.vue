<script setup lang="ts">
import { supabase } from '@/supabase';
import type { TypesFilm } from '@/types';
import AfficheFilm from '@/components/AfficheFilm.vue';

let {data : data, error} = await supabase
    .from('films')
    .select('*');

const tableauFilm = data ?? [];

</script>

<template>
    <div class="grid grid-cols-3 gap-4">
        <AfficheFilm v-for="film in tableauFilm" v-bind="film"/>
    </div>
</template>
<script setup lang="ts">
import { useRoute } from 'vue-router/auto';

import { defineProps } from 'vue';
import type { Database, Tables } from '@/supabase-types';
defineProps <Database["public"]["Tables"]["films"]["Row"] & {celebrites:Tables<'celebrites'>} & {genres:Tables<'genres'>} & {sagas:Tables<'sagas'>}  >()


</script>   

<template>

<RouterLink :to="{name:'/films/[id]', params: {id}}">
   <div class="w-[300px] m-20" >

      <img :src="affiche"/>

   </div>
</RouterLink>

   
</template>
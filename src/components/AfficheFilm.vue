<script setup lang="ts">

import { defineProps } from 'vue';
import type { TypesFilm } from '@/types';
defineProps<TypesFilm>()
</script>
<template>

   {{ titre }}
   {{ synopsis }}
   {{duree }}
   {{ saga }}
   {{ genre }}
   {{ celebrite }}
   <img :src="affiche"/>
   {{ lien }}
   
   
</template>
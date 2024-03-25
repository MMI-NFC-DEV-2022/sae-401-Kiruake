<script setup lang="ts">
import { supabase } from '@/supabase';
import { useRouter } from 'vue-router';

console.log("supabase :", supabase);

const router = useRouter();
router.replace('/films'); // Set the films route as the homepage

</script>

<template>
  <main>bonjour de home</main>
</template>



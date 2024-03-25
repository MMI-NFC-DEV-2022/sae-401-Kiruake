<script setup lang="ts">
import { supabase, user } from '../supabase';
</script>
<template>
<div>
    <button class="text-6xl  flex text-gray-200 m-auto text-center justify-center mt-72 mb-60 underline" v-if="user" @pointerdown="supabase.auth.signOut()">
        Se déconnecter ({{user.email}})
    </button>
    <button class="text-6xl  flex text-gray-200 m-auto text-center justify-center mt-72 mb-60 underline" v-else @pointerdown="supabase.auth.signInWithOAuth({provider: 'github'})">
        Se connecter avec Github
    </button>
</div>
</template>
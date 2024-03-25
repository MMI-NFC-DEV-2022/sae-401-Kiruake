<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import { onErrorCaptured } from 'vue';

onErrorCaptured((error) => {
  console.error('Error captured in global error handler:', error)
})
</script>

<template>

<Header/>

  <Suspense> 
    <RouterView />
  </Suspense>

  <Footer/>

</template>

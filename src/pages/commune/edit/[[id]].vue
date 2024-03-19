<script setup lang="ts">
import { useRoute } from 'vue-router/auto'
const route = useRoute('/commune/edit/[[id]]')
</script>
<template>
  <div class="p-2">
    <FormulaireCommune :id="route.params.id" />
  </div>
</template>
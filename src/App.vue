<script setup lang="ts">
import VHeader from './components/VHeader.vue';
import VFooter from './components/VFooter.vue';
import VPromo from './components/VPromo.vue';
import VProjects from './components/VProjects.vue';
import VTech from './components/VTech.vue';
import VFeelback from './components/VFeelback.vue';
</script>

<template>
<v-header /> 
    <main>
      <v-promo />
      <v-projects />
      <v-tech />
      <v-feelback />
      </main>
<v-footer />


</template>

<style scoped>

</style>

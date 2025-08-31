<script setup lang="ts">
import { ref } from 'vue';
import GamePage from './components/GamePage.vue';
import LandingPage from './components/LandingPage.vue';



const isStarted = ref(false);

const updateIsStarted = ()=>{
  isStarted.value = true;
}


</script>

<template>

<LandingPage v-if="!isStarted" @onClick="updateIsStarted"></LandingPage>
 <GamePage v-else></GamePage>

</template>

<style scoped>

</style>

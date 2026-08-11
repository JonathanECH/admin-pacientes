<script setup>
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import { ref } from 'vue';

const pacientes = ref([])
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Formulario />
      <div class="w-1/2 flex flex-col md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus Pacientes</h3>
        <div v-if="pacientes.length > 0"></div>
        <p v-else class="inline px-2 py-1 mt-20 border-2 border-gray-300 text-center text-2xl text-gray-500 font-semibold bg-gray-200 rounded-2xl self-center">No hay pacientes</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { uid } from 'uid';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

const pacientes = ref([])

const form = reactive({
  id: null,
  mascota: '',
  propietario: '',
  email: '',
  alta: '',
  sintomas: ''
});

//Función para guardar un paciente en el arreglo pacientes
const guardarPaciente = () => {
  pacientes.value.push({
    ...form,
    id: uid()
  }) //Para quitarle la reactivida puedes usa Spread Operator (...)
  
  //Para limpiar el formulario se usa Object.assign
  //Primero se le pasa el objeto a limpiar/ Segundo se le pasa un objeto con lo que se va a remplazar
  Object.assign(form, {
    mascota: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: ''
  })
}
</script>

<template>
  <div class="container mx-auto mt-20">

    <Header />
    <!--* Componente del Header -->

    <div class="mt-12 md:flex gap-3">

      <Formulario v-model:mascota="form.mascota" v-model:propietario="form.propietario" v-model:email="form.email"
        v-model:alta="form.alta" v-model:sintomas="form.sintomas" @guardar-paciente="guardarPaciente" />
      <!--* Componente del Formulario -->

      <div class="w-1/2 flex flex-col md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus Pacientes</h3>
        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10">Información de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>

          <Paciente v-for="paciente in pacientes" :paciente="paciente" />
          <!--* Componente del Paciente -->

        </div>
        <p v-else
          class="inline px-2 py-1 border-2 border-gray-300 mt-22
          text-center text-2xl text-gray-500 font-semibold bg-gray-200 rounded-2xl self-center">
          No hay pacientes</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted, watch } from 'vue';
import { uid } from 'uid';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

const pacientes = ref([])
const isEditar = ref(false)
const form = reactive({
  id: null,
  mascota: '',
  propietario: '',
  email: '',
  alta: '',
  sintomas: ''
});

watch(pacientes, () => {
  guardarLocalStorage()
}, {
  deep: true
})

onMounted(() => {
  const pacientesLocalStorage = localStorage.getItem('pacientes')
  if(pacientesLocalStorage){
    pacientes.value = JSON.parse(pacientesLocalStorage)
  }
})

//Función para guardar un paciente en el arreglo pacientes
const guardarPaciente = () => {
  if (form.id) {
    const index = pacientes.value.findIndex(paciente => paciente.id === form.id)
    pacientes.value[index] = { ...form }
  } else {
    pacientes.value.push({
      ...form,
      id: uid()
    }) //Para quitarle la reactivida puedes usa Spread Operator (...)
  }

  //Para limpiar el formulario se usa Object.assign
  //Primero se le pasa el objeto a limpiar/ Segundo se le pasa un objeto con lo que se va a remplazar
  Object.assign(form, {
    mascota: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: '',
    id: null
  })
}

const editarPaciente = id => {
  const pacienteAEditar = pacientes.value.find((paciente) => paciente.id === id);
  if (pacienteAEditar) {
    Object.assign(form, pacienteAEditar);//Se usa Object.assign para llevar los datos del paciente al form
    isEditar.value = true
  }
}

const guardarLocalStorage = () => {
  localStorage.setItem('pacientes', JSON.stringify(pacientes.value))
}
</script>

<template>
  <div class="container mx-auto mt-20">

    <Header />
    <!--* Componente del Header -->

    <div class="mt-12 md:flex gap-3">

      <Formulario v-model:mascota="form.mascota" v-model:propietario="form.propietario" v-model:email="form.email"
        v-model:alta="form.alta" v-model:sintomas="form.sintomas" @guardar-paciente="guardarPaciente"
        :isEditar="isEditar" />
      <!--* Componente del Formulario -->

      <div class="w-1/2 flex flex-col md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus Pacientes</h3>
        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10">Información de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>

          <Paciente v-for="paciente in pacientes" :paciente="paciente" @editar-paciente="editarPaciente" />
          <!--* Componente del Paciente -->

        </div>
        <p v-else class="inline px-2 py-1 border-2 border-gray-300 mt-22
          text-center text-2xl text-gray-500 font-semibold bg-gray-200 rounded-2xl self-center">
          No hay pacientes</p>
      </div>
    </div>
  </div>
</template>

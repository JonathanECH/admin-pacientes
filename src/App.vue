<script setup>
import { ref, reactive, onMounted, watch } from 'vue';
import { uid } from 'uid';
import Header from './components/Header.vue';
import Formulario from './components/Formulario.vue';
import Paciente from './components/Paciente.vue';

const pacientes = ref([])
const formScroll = ref(null)
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
  if (pacientesLocalStorage) {
    pacientes.value = JSON.parse(pacientesLocalStorage)
  }
})

//Objeto que almacena las alertas
const alerta = reactive({
  tipo: '',
  mensaje: ''
})

//Función para mostrar el mensaje en el form
const mostrarAlerta = (tipo, mensaje) => {
  alerta.mensaje = mensaje
  alerta.tipo = tipo
  //Limpiamos el mensaje después de 5 segundos
  setTimeout(() => {
    alerta.mensaje = ''
    alerta.tipo = ''
  }, 5000);
}

//Función para guardar un paciente en el arreglo pacientes
const guardarPaciente = () => {
  if (form.id) {
    const index = pacientes.value.findIndex(paciente => paciente.id === form.id)
    pacientes.value[index] = { ...form }
    mostrarAlerta('success', 'Paciente editado correctamente')//Mostramos el mensaje de éxito
  } else {
    pacientes.value.push({
      ...form,
      id: uid()
    }) //Para quitarle la reactividad se usa Spread Operator (...)
    mostrarAlerta('success', 'Paciente registrado correctamente')//Mostramos el mensaje de éxito
  }

  //Para limpiar el formulario se usa Object.assign
  //Primero se le pasa el objeto a limpiar y segundo, un objeto con lo que se va a reemplazar
  Object.assign(form, {
    mascota: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: '',
    id: null
  })
}

//Función para editar un paciente
const editarPaciente = id => {
  const pacienteAEditar = pacientes.value.find((paciente) => paciente.id === id);
  if (pacienteAEditar) {
    Object.assign(form, pacienteAEditar);//Se usa Object.assign para llevar los datos del paciente al form
    formScroll.value.$el.scrollIntoView({ behavior: 'smooth' })
  }
}

//Función para eliminar un paciente
const eliminarPaciente = id => {
  pacientes.value = pacientes.value.filter(paciente => paciente.id !== id)
  mostrarAlerta('success', 'Paciente eliminado correctamente')
  formScroll.value.$el.scrollIntoView({ behavior: 'smooth' })
}

const guardarLocalStorage = () => {
  localStorage.setItem('pacientes', JSON.stringify(pacientes.value))
}
</script>

<template>
  <div class="container mx-auto mt-20">

    <Header />
    <!--* Componente del Header -->

    <div class="mt-12 mx-5 md:flex gap-5">

      <Formulario ref="formScroll" v-model:mascota="form.mascota" v-model:propietario="form.propietario"
        v-model:email="form.email" v-model:alta="form.alta" v-model:sintomas="form.sintomas"
        @guardar-paciente="guardarPaciente" @mostrar-alerta="mostrarAlerta" :alerta="alerta" :id="form.id" />
      <!--* Componente del Formulario -->

      <div class="md:w-1/2 flex flex-col md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus Pacientes</h3>
        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10">Información de
            <span class="text-indigo-600 font-bold">Pacientes</span>
          </p>

          <Paciente v-for="paciente in pacientes" :paciente="paciente" @editar-paciente="editarPaciente"
            @eliminar-paciente="eliminarPaciente" />
          <!--* Componente del Paciente -->

        </div>
        <p v-else class="inline px-2 py-1 border-2 border-gray-300 mt-22
          text-center text-2xl text-gray-500 font-semibold bg-gray-200 rounded-2xl self-center">
          No hay pacientes</p>
      </div>
    </div>
  </div>
</template>

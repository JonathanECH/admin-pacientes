<script setup>
import { computed, reactive } from 'vue';
import Alerta from './Alerta.vue'


//Objeto que almacena las alertas
const alerta = reactive({
    tipo: '',
    mensaje: ''
})

//Definimos los Emits
const emit = defineEmits(['update:mascota', 'update:propietario', 'update:email',
    'update:alta', 'update:sintomas', 'guardar-paciente'])

//Definimos los Props
const props = defineProps({
    id: {
        type: [String, null],
        required: true
    },
    mascota: {
        type: String,
        required: true
    },
    propietario: {
        type: String,
        required: true
    },
    email: {
        type: String,
        required: true
    },
    alta: {
        type: String,
        required: true
    },
    sintomas: {
        type: String,
        required: true
    }
})

//Validamos los campos del form
const validarForm = () => {
    if (Object.values(props).includes('')) {
        mostarAlerta('error', 'Todos los campos son obligatorios')//Mostramos el mensaje de error
        return
    }
    emit('guardar-paciente')
    mostarAlerta('success', 'Paciente registrado correctamente')//Mostramos el mensaje de éxito
}

const mostarAlerta = (tipo, mensaje) => {
    alerta.mensaje = mensaje
    alerta.tipo = tipo
    //Limpiamos el mensaje después de 5 segundos
    setTimeout(() => {
        alerta.mensaje = ''
        alerta.tipo = ''
    }, 5000);
}

const editando = computed(() => {
    return props.id
})
</script>

<template lang="">
    <div class="md:w-1/2 lg:w-4xl mb-10">
        <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
        <p class="text-lg mt-5 text-center mb-10">Añade Pacientes y
            <span class="text-indigo-600 font-bold">Adminístralos</span>
        </p>

        <form class="bg-white shadow-md rounded-lg p-5"
        @submit.prevent="validarForm">

            <!--* Aquí se mostrarán los mensajes de error o éxito -->
            <Alerta v-if="alerta.mensaje" :alerta="alerta" />

            <div class="mb-5">
                <label for="mascota" class="block font-bold text-gray-600 uppercase mt-5">Nombre Mascota</label>
                <input 
                id="mascota"
                type="text"
                class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Nombre de la Mascota"
                :value="mascota"
                @input="$emit('update:mascota', $event.target.value)"></input>
            </div>

            <div class="mb-5">
                <label for="propietario" class="block font-bold text-gray-600 uppercase mt-5">Nombre Propietario</label>
                <input 
                id="propietario"
                type="text"
                class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Nombre del Propietario"
                :value="propietario"
                @input="$emit('update:propietario', $event.target.value)"></input>
            </div>

            <div class="mb-5">
                <label for="email" class="block font-bold text-gray-600 uppercase mt-5">Email</label>
                <input 
                id="email"
                type="email"
                class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Email de contacto del Propietario"
                :value="email"
                @input="$emit('update:email', $event.target.value)"></input>
            </div>

            <div class="mb-5">
                <label for="alta" class="block font-bold text-gray-600 uppercase mt-5">Alta</label>
                <input 
                id="alta"
                type="date"
                class="w-full border-gray-100 rounded-md border-2 p-3 cursor-pointer
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                :value="alta"
                @input="$emit('update:alta', $event.target.value)"></input>
            </div>

            <div class="mb-5">
                <label for="sintomas" class="block font-bold text-gray-600 uppercase mt-5">Síntomas</label>
                <textarea 
                id="sintomas"
                class="w-full border-gray-100 rounded-md border-2 p-3 resize-none
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Síntomas del Paciente"
                :value="sintomas"
                @input="$emit('update:sintomas', $event.target.value)"/>
            </div>

            <input type="submit" class="w-full rounded-md mt-5 text-white text-lg uppercase bg-indigo-600 hover:bg-indigo-700 hover:translate-y-1 transition-all duration-300 ease-in-out box-border border border-transparent focus:outline-none font-bold leading-5 px-4 py-2.5 inline-flex items-center justify-center cursor-pointer shadow-md" :value="[editando ? 'Editar Paciente': 'Registrar Paciente']"></input>
        </form>
        <!--? Formulario -->
    </div>
</template>

<script setup>
import { reactive } from 'vue';
import Alerta from './Alerta.vue'

const form = reactive({
    mascota: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: ''
});

//Objeto que almacena las alertas
const alerta = reactive({
    tipo: '',
    mensaje: ''
})

//Validamos los campos del form
const validarForm = () => {
    if (Object.values(form).includes('')) {
        mostarAlerta('error', 'Todos los campos son obligatorios')//Mostramos el mensaje de error
        return
    }
    mostarAlerta('success', 'Paciente registrado correctamente')//Mostramos el mensaje de éxito
    console.log('Formulario enviado')
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
</script>

<template lang="">
    <div class="md:w-1/2 mb-10">
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
                <input id="mascota" type="text" class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Nombre de la Mascota"
                v-model="form.mascota"></input>
            </div>

            <div class="mb-5">
                <label for="propietario" class="block font-bold text-gray-600 uppercase mt-5">Nombre Propietario</label>
                <input id="propietario" type="text" class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Nombre del Propietario"   
                v-model="form.propietario"></input>
            </div>

            <div class="mb-5">
                <label for="email" class="block font-bold text-gray-600 uppercase mt-5">Email</label>
                <input id="email" type="text" class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Email de contacto del Propietario"
                v-model="form.email"></input>
            </div>

            <div class="mb-5">
                <label for="alta" class="block font-bold text-gray-600 uppercase mt-5">Alta</label>
                <input id="alta" type="date" class="w-full border-gray-100 rounded-md border-2 p-3 cursor-pointer
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium" 
                v-model="form.alta"></input>
            </div>

            <div class="mb-5">
                <label for="sintomas" class="block font-bold text-gray-600 uppercase mt-5">Síntomas</label>
                <textarea id="sintomas" class="w-full border-gray-100 rounded-md border-2 p-3 resize-none
                placeholder:text-lg placeholder:text-gray-500 placeholder:font-medium"
                placeholder="Síntomas del Paciente"
                v-model="form.sintomas"/>
            </div>

            <input type="submit" class="w-full rounded-md mt-5 text-white text-lg uppercase bg-indigo-600 hover:bg-indigo-700 hover:translate-y-1 transition-all duration-300 ease-in-out box-border border border-transparent focus:outline-none font-bold leading-5 px-4 py-2.5 inline-flex items-center justify-center cursor-pointer shadow-md" value="Reguistrar Paciente"></input>
        </form>
        <!--? Formulario -->
    </div>
</template>

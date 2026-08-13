<script setup>
//Defino el prop para el array
const props = defineProps({
    paciente: {
        type: Object,
        required: true
    }
})

//Defino los emits para eliminar ó editar un paciente
const emit = defineEmits(['editar-paciente', 'mostrar-modal'])
</script>
<template lang="">
<div class="my-10 bg-white dark:bg-gray-800 shadow-md px-5 py-10 rounded-xl">
        <p class="font-bold mb-3 text-gray-700 dark:text-gray-300 uppercase">ID:
            <span class="font-normal normal-case">
            {{paciente.id}}
            </span>
        </p>

        <p class="font-bold mb-3 text-gray-700 dark:text-gray-300 uppercase">Nombre:
            <span class="font-normal normal-case">
            {{paciente.mascota}}
            </span>
        </p>

        <p class="font-bold mb-3 text-gray-700 dark:text-gray-300 uppercase">Propietario: 
            <span class="font-normal normal-case">
            {{paciente.propietario}}
            </span>
        </p>

        <p class="font-bold mb-3 text-gray-700 dark:text-gray-300 uppercase">Email: 
            <span class="font-normal normal-case">
            {{paciente.email}}
            </span>
        </p>

        <p class="font-bold mb-3 text-gray-700 dark:text-gray-300 uppercase">Fecha Alta:
            <span class="font-normal normal-case">
            {{paciente.alta}}
            </span>
        </p>

        <p class="font-bold mb-3 text-gray-700 dark:text-gray-300 uppercase">Síntomas:
            <span class="font-normal normal-case">
            {{paciente.sintomas}}
            </span>
        </p>

        <div class="grid md:grid-cols-2  gap-5 mt-10 ">
            <button 
                type="button"
                class="block w-full py-2 px-10 bg-indigo-600 hover:bg-indigo-700
                cursor-pointer text-white font-bold uppercase rounded-lg"
                @click="$emit('editar-paciente', paciente.id)"
            >Editar</button>

            <button 
                type="button"
                class="block w-full py-2 px-10 bg-red-600 hover:bg-red-700
                cursor-pointer text-white font-bold uppercase rounded-lg"
                @click="$emit('mostrar-modal', paciente.id)"
            >Eliminar</button>
        </div>
    </div>
</template>
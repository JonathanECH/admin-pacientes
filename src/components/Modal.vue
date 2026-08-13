<script setup>
//Se definen las props que se van a recibir
const props = defineProps({
    modal: {
        type: Boolean,
        required: true
    }
})
//Se definen los emits que se van a enviar
const emit = defineEmits(['close-modal', 'delete-paciente'])
</script>
<template>
    <div v-if="modal"
        class="fixed inset-0 z-50 flex items-center justify-center bg-black/50 p-4 transition-opacity duration-300 ease-in-out">
        <div class="bg-white dark:bg-gray-800 rounded-lg shadow-xl p-8 max-w-md w-full transform transition-all duration-300 ease-in-out">
            <h3 class="font-bold text-2xl text-center text-gray-800 dark:text-gray-100 mb-6">¿Confirmar Eliminación?</h3>
            <p class="text-gray-600 dark:text-gray-300 text-center mb-8">Un paciente eliminado no se puede recuperar.</p>
            <div class="flex justify-center gap-4">
                <button @click="$emit('close-modal')" type="button"
                    class="w-full py-2 px-10 bg-gray-600 hover:bg-gray-700 cursor-pointer text-white font-bold uppercase rounded-lg transition-colors duration-300">
                    Cancelar
                </button>
                <button @click="$emit('delete-paciente')" type="button"
                    class="w-full py-2 px-10 bg-red-600 hover:bg-red-700 cursor-pointer text-white font-bold uppercase rounded-lg transition-colors duration-300">
                    Eliminar
                </button>
            </div>
        </div>
    </div>
</template>
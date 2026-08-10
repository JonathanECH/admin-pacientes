<script setup>
import { computed } from 'vue'
//Se definen las props que se van a recibir
const props = defineProps({
    alerta: {
        type: Object,
        required: true
    }
})

//Con computed, comprobamos si el tipo es error o éxito
const isError = computed(() => props.alerta.tipo === 'error')
</script>
<template>
    <!-- Con el v-if, se muestra el mensaje de error o éxito -->
    <div :class="[isError ? 'bg-red-500' : 'bg-green-500']"
        class="text-white text-center p-3 uppercase font-bold mb-3 rounded-md">
        {{ alerta.mensaje }}
    </div>
</template>
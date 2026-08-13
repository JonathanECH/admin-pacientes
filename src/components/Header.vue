<script setup>
const props = defineProps({
    isDark: {
        type: Boolean,
        required: true
    }
})

const emit = defineEmits(['toggle-dark-mode'])
</script>
<template>
    <div class="flex justify-center items-center gap-4 mb-4 md:mb-0">
        <h1 class="font-black text-5xl text-center dark:text-gray-100 transition-colors duration-300">Seguimiento pacientes
            <span class="text-indigo-600 dark:text-indigo-400">Veterinaria</span>
        </h1>
        <button @click="$emit('toggle-dark-mode')"
            class="hidden lg:block p-2 md:self-end relative bottom-0 text-gray-600 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-800 rounded-full cursor-pointer transition-colors duration-200"
            aria-label="Toggle dark mode">
            <!-- Icono de Sol (Modo Oscuro Activo) -->
            <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round"
                    d="M12 3v2.25m0 13.5V23M4.22 4.22l1.58 1.58m12.42 12.42l1.58 1.58M3 12h2.25m13.5 0H23M4.22 19.78l1.58-1.58M17.66 6.34l1.58-1.58M12 7.5a4.5 4.5 0 1 0 0 9 4.5 4.5 0 0 0 0-9Z" />
            </svg>

            <!-- Icono de Luna (Modo Claro Activo) -->
            <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
                class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round"
                    d="M21.752 15.002A9.72 9.72 0 0 1 18 15.75c-5.385 0-9.75-4.365-9.75-9.75 0-1.33.266-2.597.748-3.752A9.753 9.753 0 0 0 3 11.25C3 16.635 7.365 21 12.75 21a9.753 9.753 0 0 0 9.002-5.998Z" />
            </svg>
        </button>
    </div>

    <!-- Botón flotante para móviles y tablets -->
    <button @click="$emit('toggle-dark-mode')"
        class="block lg:hidden fixed bottom-4 right-4 z-50 p-3 bg-white dark:bg-gray-800 shadow-lg rounded-full cursor-pointer transition-colors duration-200 border border-gray-200 dark:border-gray-700"
        aria-label="Toggle dark mode">
        <!-- Icono de Sol (Modo Oscuro Activo) -->
        <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
            stroke="currentColor" class="w-6 h-6 text-gray-600 dark:text-gray-300">
            <path stroke-linecap="round" stroke-linejoin="round"
                d="M12 3v2.25m0 13.5V23M4.22 4.22l1.58 1.58m12.42 12.42l1.58 1.58M3 12h2.25m13.5 0H23M4.22 19.78l1.58-1.58M17.66 6.34l1.58-1.58M12 7.5a4.5 4.5 0 1 0 0 9 4.5 4.5 0 0 0 0-9Z" />
        </svg>

        <!-- Icono de Luna (Modo Claro Activo) -->
        <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
            class="w-6 h-6 text-gray-600 dark:text-gray-300">
            <path stroke-linecap="round" stroke-linejoin="round"
                d="M21.752 15.002A9.72 9.72 0 0 1 18 15.75c-5.385 0-9.75-4.365-9.75-9.75 0-1.33.266-2.597.748-3.752A9.753 9.753 0 0 0 3 11.25C3 16.635 7.365 21 12.75 21a9.753 9.753 0 0 0 9.002-5.998Z" />
        </svg>
    </button>
</template>
<script>
export default {

}
</script>

<template lang="">
    <div class="md:w-1/2 mb-10">
        <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
        <p class="text-lg mt-5 text-center mb-10">Añade Pacientes y
            <span class="text-indigo-600 font-bold">Adminístralos</span>
        </p>

        <form class="bg-white shadow-md rounded-lg p-5">
            <label class="block font-bold mb-2 text-gray-600 uppercase mt-5">Nombre Mascota</label>
            <input type="text" class="w-full border-gray-100 rounded-md border-2 p-3
            placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
            placeholder="Nombre de la Mascota"></input>

            <label class="block font-bold mb-2 text-gray-600 uppercase mt-5">Nombre Propietario</label>
            <input type="text" class="w-full border-gray-100 rounded-md border-2 p-3
            placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
            placeholder="Nombre del Propietario"></input>

            <label class="block font-bold mb-2 text-gray-600 uppercase mt-5">Email</label>
            <input type="text" class="w-full border-gray-100 rounded-md border-2 p-3
            placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
            placeholder="Email de contacto del Propietario"></input>

            <label class="block font-bold mb-2 text-gray-600 uppercase mt-5">Alta</label>
            <input type="date" class="w-full border-gray-100 rounded-md border-2 p-3 cursor-pointer
            placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"></input>
            
            <label class="block font-bold mb-2 text-gray-600 uppercase mt-5">Síntomas</label>
            <textarea class="w-full border-gray-100 rounded-md border-2 p-3 resize-none
            placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
            placeholder="Síntomas del Paciente"></textarea>

            <button type="submit" class="border border-indigo-600 w-full
            text-white p-3 rounded-2xl mt-5 hover:bg-amber-300">Registrar</button>
        </form>
    </div>
</template>

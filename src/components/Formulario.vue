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
            <div class="mb-5">
                <label for="mascota" class="block font-bold text-gray-600 uppercase mt-5">Nombre Mascota</label>
                <input id="mascota" type="text" class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
                placeholder="Nombre de la Mascota"></input>
            </div>

            <div class="mb-5">
                <label for="propietario" class="block font-bold text-gray-600 uppercase mt-5">Nombre Propietario</label>
                <input id="propietario" type="text" class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
                placeholder="Nombre del Propietario"></input>
            </div>

            <div class="mb-5">
                <label for="email" class="block font-bold text-gray-600 uppercase mt-5">Email</label>
                <input id="email" type="text" class="w-full border-gray-100 rounded-md border-2 p-3
                placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
                placeholder="Email de contacto del Propietario"></input>
            </div>

            <div class="mb-5">
                <label for="alta" class="block font-bold text-gray-600 uppercase mt-5">Alta</label>
                <input id="alta" type="date" class="w-full border-gray-100 rounded-md border-2 p-3 cursor-pointer
                placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"></input>
            </div>

            <div class="mb-5">
                <label for="sintomas" class="block font-bold text-gray-600 uppercase mt-5">Síntomas</label>
                <textarea id="sintomas" class="w-full border-gray-100 rounded-md border-2 p-3 resize-none
                placeholder:text-lg placeholder:text-gray-400 placeholder:font-semibold"
                placeholder="Síntomas del Paciente"/>
            </div>

            <input type="submit" class="w-full rounded-md mt-5 text-white text-lg uppercase bg-indigo-600 hover:bg-indigo-700 hover:translate-y-1 transition-all duration-300 ease-in-out box-border border border-transparent focus:outline-none font-bold leading-5 px-4 py-2.5 inline-flex items-center justify-center cursor-pointer shadow-md" value="Reguistrar Paciente"></input>
        </form>
    </div>
</template>

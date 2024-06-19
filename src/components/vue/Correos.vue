<script setup>
import { ref } from 'vue';


const emails = ref([
    { title: "Correo 1", text: "Texto del correo 1", time: "Hace 1 hora", estado: false, snd:true },
    { title: "Correo 2", text: "Texto del correo 2", time: "Hace 1 hora", estado: false, snd:true },
    { title: "Correo 3", text: "Texto del correo 3", time: "Hace 2 hora", estado: false, snd:true },
    { title: "Correo 4", text: "Texto del correo 4", time: "Hace 3 hora", estado: false, snd:true },
])

function select(index) {
emails.value[index].estado=!emails.value[index].estado

}

function marcar(index) {
    emails.value[index].snd=false
}

</script>

<template>

    <div class="m-0 p-0 border-black border ">
        <h1 class="text-lg text-center">Correos</h1>

        <div v-for="(email, index) in emails" :key="index" :class="{'border-blue-500':email.estado}"
            class="bg-white/60 border-2 px-2 m-2 p-2 w-[25%] h-max text-start mx-auto hover:border-blue-500 ">

            <div id="caja" class="flex" @click="select(index)">
                <div class="p-2 m-2 items-center">
                    <svg xmlns="http://www.w3.org/2000/svg" height="50" width="50" viewBox="0 0 512 512"><path d="M256 512A256 256 0 1 0 256 0a256 256 0 1 0 0 512zm0-384c13.3 0 24 10.7 24 24V264c0 13.3-10.7 24-24 24s-24-10.7-24-24V152c0-13.3 10.7-24 24-24zM224 352a32 32 0 1 1 64 0 32 32 0 1 1 -64 0z"/></svg>
                </div>
                <div class="flex-auto">
                    <div class="flex justify-between">

                        <span class="font-serif" :class="{'font-black':email.snd}">{{ email.title }}</span>

                        <button @click="marcar(index)" v-show="email.estado && email.snd"
                            class=" text-center w-max text-xs text-gray-300" >Marcar
                            como leido</button>

                    </div>
                    <span>{{ email.text }}</span>
                    <p class="text-gray-400 text-xs">{{ email.time }}</p>
                </div>
            </div>

        </div>

    </div>
</template>
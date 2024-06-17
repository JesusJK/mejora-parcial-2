<script setup>
import { ref } from 'vue';

const emails = ref([
    { title: "Correo 1", text: "Texto del correo 1", time: "Hace 1 hora", estado: false, negrilla: 'font-black', borde: 'border-gray-400', snd:true },
    { title: "Correo 2", text: "Texto del correo 2", time: "Hace 1 hora", estado: false, negrilla: 'font-black', borde: 'border-gray-400', snd:true },
    { title: "Correo 3", text: "Texto del correo 3", time: "Hace 2 hora", estado: false, negrilla: 'font-black', borde: 'border-gray-400', snd:true },
    { title: "Correo 4", text: "Texto del correo 4", time: "Hace 3 hora", estado: false, negrilla: 'font-black', borde: 'border-gray-400', snd:true },
])

function select(index) {
emails.value[index].estado=!emails.value[index].estado
if (emails.value[index].estado == true) {
    emails.value[index].borde = 'border-blue-500'
} else if(emails.value[index].estado == false){
    emails.value[index].borde = 'border-gray-400'
}

}

function marcar(index) {
    emails.value[index].snd=false
    emails.value[index].negrilla='font-serif'
}

</script>

<template>
    <div class="m-0 p-0 border-black border ">
        <h1 class="text-lg text-center">Correos</h1>

        <div v-for="(email, index) in emails" :key="index" :class="email.borde"
            class="bg-white/60 border-2 px-2 m-2 p-2 w-[25%] h-max text-start mx-auto hover:border-blue-500 ">

            <div id="caja" class="flex" @click="select(index)">
                <div class="p-2 m-2 items-center"></div>
                <div class="flex-auto">
                    <div class="flex justify-between">

                        <span :class="email.negrilla">{{ email.title }}</span>

                        <button @click="marcar(index)" v-show="email.estado && email.snd"
                            class=" text-center w-max text-xs text-gray-300">Marcar
                            como leido</button>

                    </div>
                    <span>{{ email.text }}</span>
                    <p class="text-gray-400 text-xs">{{ email.time }}</p>
                </div>
            </div>

        </div>

    </div>
</template>
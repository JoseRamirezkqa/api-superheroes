<template>
    <div class=" flex justify-center animar w-[100%] ">
        <div
            class="fixed border text-center border-2 border-black mt-[30px] z-[100] w-[30%] h-[100px] duration-300 bg-white">
            <h1 class="text-2xl mt-[5px] font-bold">
                {{ text }}
            </h1>
            <button class="bg-[#FB4747] w-[100px] mt-[10px] hover:bg-[#D00F0F] duration-300 rounded-full 
                        border border-[2.5px] border-black transition ease-in-out delay-150 hover:scale-110"
                @click="cerrar">
                Cerrar
            </button>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        text: {
            type: String
        }
    },
    methods: {
        cerrar() {
            this.$emit('cambia')
        },
    }
}
</script>
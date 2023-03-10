<template>
    <div class="border border-black justify-self-center shadow-slate-500 shadow-xl mb-[20px] w-[95%] h-[400px] 
                                grid grid-cols-2 justify-items-center ">
        <img :src="link" alt="No hay una imagen" class="w-[250px] shadow-slate-500 shadow-lg ">
        <div class="px-[10px] py-[5px]">
            <div>
                <h1 class="font-bold inline-block mr-[5px]">Name:</h1>
                <h1 class="font-normal inline-block">{{ name }}</h1>
            </div>
            <div>
                <h1 class="font-bold inline-block mr-[5px]">Race: </h1>
                <h1 class="font-normal inline-block">{{ race }}</h1>
            </div>
            <div>
                <h1 class="font-bold inline-block mr-[5px]">Occupation: </h1>
                <h1 class="font-normal inline-block">{{ occupation }}</h1>
            </div>
        </div>
        <h1 class="text-4xl font-black pt-[10px]">Id: {{ idn }} </h1>
        <nuxt-link class="bg-[#FB4747] w-[150px] mt-[10px] hover:bg-[#D00F0F] duration-500 
                    rounded-full border border-[2.5px] border-black h-[50px] items-center flex  
                    justify-center transition ease-in-out delay-150 hover:scale-110"  :to="to">
                    Ver más
        </nuxt-link>
    </div>
</template>
<script>
export default {
    props: {
        link: String,
        race: String,
        name: String,
        idn: String,
        occupation: String,
        to: String,
    }
}
</script>
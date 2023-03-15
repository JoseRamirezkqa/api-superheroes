<template>
    <div class="border border-black justify-self-center shadow-slate-500 shadow-xl mb-[0.625rem] 2xl:mb-[1.25rem] w-[95%] 2xl:h-[25rem] 
                        grid 2xl:grid-cols-2 justify-items-center animate__animated animate__zoomIn animate__slower">
        <img :src="link" alt="No hay una imagen" class="2xl:w-[15.625rem] shadow-slate-500 shadow-lg my-[0.625rem] w-[95%] h-[598px] 2xl:h-[292px]">
        <div class="2xl:px-[0.625rem] 2xl:py-[0.313rem] mb-[0.625rem] mx-[0.938rem] w-[95%]">
            <div>
                <h1 class="font-bold inline-block 2xl:mr-[0.313rem]">Name:</h1>
                <h1 class="font-normal inline-block">{{ name }}</h1>
            </div>
            <div>
                <h1 class="font-bold inline-block 2xl:mr-[0.313rem]">Race: </h1>
                <h1 class="font-normal inline-block">{{ race }}</h1>
            </div>
            <div>
                <h1 class="font-bold inline-block 2xl:mr-[0.313rem]">Occupation: </h1>
                <h1 class="font-normal inline-block">{{ occupation }}</h1>
            </div>
        </div>
        <h1 class="text-4xl font-black 2xl:pt-[0.625rem]">Id: {{ idn }} </h1>
        <nuxt-link class="bg-[rgb(251,71,71)] 2xl:w-[9.375rem] 2xl:mt-[0.625rem] hover:bg-[#D00F0F] duration-500 
                    rounded-full  2xl:border-[0.156rem] border-black 2xl:h-[3.125rem] items-center flex  
                    justify-center transition ease-in-out delay-150 hover:scale-110 h-[3.125rem] w-[6.25rem] my-[0.938rem]" :to="to">
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
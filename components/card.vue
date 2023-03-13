<template>
    <div class="border border-black justify-self-center shadow-slate-500 shadow-xl mb-[0.625rem] sm:mb-[1.25rem] w-[95%] sm:h-[25rem] 
                        grid sm:grid-cols-2 justify-items-center animate__animated animate__zoomIn animate__slower">
        <img :src="link" alt="No hay una imagen" class="sm:w-[15.625rem] shadow-slate-500 shadow-lg my-[0.625rem] w-[95%]">
        <div class="sm:px-[0.625rem] sm:py-[0.313rem] mb-[0.625rem] mx-[0.938rem] w-[95%]">
            <div>
                <h1 class="font-bold inline-block sm:mr-[0.313rem]">Name:</h1>
                <h1 class="font-normal inline-block">{{ name }}</h1>
            </div>
            <div>
                <h1 class="font-bold inline-block sm:mr-[0.313rem]">Race: </h1>
                <h1 class="font-normal inline-block">{{ race }}</h1>
            </div>
            <div>
                <h1 class="font-bold inline-block sm:mr-[0.313rem]">Occupation: </h1>
                <h1 class="font-normal inline-block">{{ occupation }}</h1>
            </div>
        </div>
        <h1 class="text-4xl font-black sm:pt-[0.625rem]">Id: {{ idn }} </h1>
        <nuxt-link class="bg-[rgb(251,71,71)] sm:w-[9.375rem] sm:mt-[0.625rem] hover:bg-[#D00F0F] duration-500 
                    rounded-full  sm:border-[0.156rem] border-black sm:h-[3.125rem] items-center flex  
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
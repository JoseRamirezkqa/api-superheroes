<template>
    <div class=" sm:w-[37.5rem] sm:h-[37.5rem] m-auto grid justify-items-center sm:mt-[3.125rem]">
        <h1 class="text-[#bd2929] font-bold text-2xl">could not find superhero</h1>
        <div class="bg-error sm:w-[37.5rem] sm:h-[37.5rem]  bg-no-repeat bg-cover bg-center">
        </div>
        <div>
            <nuxt-link class="bg-[rgb(251,71,71)] sm:w-[9.375rem] sm:mt-[0.625rem] hover:bg-[#D00F0F] duration-500 
                    rounded-full  sm:border-[0.156rem] border-black sm:h-[3.125rem] items-center flex  
                    justify-center transition ease-in-out delay-150 hover:scale-110  "  to="/">
                    Volver
        </nuxt-link>

        </div>
   </div>
</template>
<script>
  export default {
    props: ['error'],
    layout: 'error'
  }
</script>
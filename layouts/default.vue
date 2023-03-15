<template>
  <div>
    <div class="w-[100%] bg-gray-100 2xl:h-[4.375rem]  items-center	grid grid-cols-3">
      <div class="2xl:col-span-1 col-span-2">
        <div class="inline-block 2xl:mx-[1.25rem]">
          <h1 class="font-bold 2xl:text-xl text-lg">
            SUPERHERO API
          </h1>
        </div>
        <div class="inline-block ">
          <h1 class="font-bold 2xl:text-xl text-lg hover:text-stone-500 duration-500">
            <nuxtLink to="/">| HOME</nuxtLink>
          </h1>
        </div>
      </div>
      <div class="2xl:col-span-2	justify-self-end	2xl:mr-[3.125rem] my-[0.313rem]">
        <div class="flex border  duration-300 rounded-full 2xl:w-[15.625rem] 2xl:h-[2.5rem] justify-center 
                                      items-center focus-within:border-black w-[15rem] h-[3.125rem]">
          <img src="../static/icons8-búsqueda-50.png" class="2xl:w-[1.875rem] 2xl:h-[1.875rem] 2xl:mr-[0.188rem] w-[1.8rem]" alt="No sirve esta mierda">
          <input type="text" v-model="busquedaPalabra" placeholder="shearch"
            class="2xl:h-[1.875rem] 2xl:w-[12.5rem] w-[10rem] bg-gray-100 focus:outline-0" @keydown.enter="busqueda">
        </div>
      </div>
    </div>
    <Nuxt class="animate__animated animate__zoomIn animate__slower"/>
  </div>
</template>
<script>
export default {
  name: "LayoutDefault",
  data() {
    return {
      url: `https://www.superheroapi.com/api.php/5924508177585115/search`,
      busquedaPalabra: '',
      name: '',
      id: '',
    }
  },
  methods: {
    async busqueda() {
      if (this.busquedaPalabra != '') {
        const response = await this.$axios.get(this.url + `/${this.busquedaPalabra}`)
        console.log(response.data.response)
        if (response.data.response == "success") {
          this.id = response.data.results[0].id
          this.$router.push(`${this.id}`)
        } else if (response.data.response == "error") {
          this.$router.push(`error`)

        }
        this.busquedaPalabra = ''

      }
    },

  }
}
</script>
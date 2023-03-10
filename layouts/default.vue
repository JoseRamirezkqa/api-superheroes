<template>
  <div id="default">
    <div class="w-[100%] bg-gray-100 h-[70px]  items-center	">
      <div class="inline-block">
        <h1 class="font-bold">
          API DE SUPERHEROES
        </h1>
      </div>
      <div class="inline-block">
        <h1 class="font-bold hover:text-stone-500 duration-500">
          INCIO
        </h1>
      </div>
      <div>
        <div class="flex border  duration-300 rounded-full w-[250px] h-[40px] justify-center 
                                  items-center focus-within:border-black ">
          <img src="../static/icons8-búsqueda-50.png" class="w-[30px] h-[30px] mr-[3px]" alt="No sirve esta mierda">
          <input type="text" v-model="busquedaPalabra" placeholder="busqueda"
            class="h-[30px] w-[200px] bg-gray-100 focus:outline-0" @keydown.enter="busqueda">
        </div>
      </div>
    </div>
    <modales text='No se encontró el super héroe' v-if="bandera" @cambia="cerrar" :class="{ animar: active }" />
    <Nuxt :class="{ per: activeDos }" />
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
      bandera: false,
      active: false,
      activeDos: false,
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
          this.bandera = true
          this.active = true
          this.activeDos = true
        }
        this.busquedaPalabra = ''

      }
    },
    cerrar() {
      this.bandera = false
      this.activeDos = false
    }
  }
}
</script>
<style>
.animar {
  -webkit-animation-name: animarsuperior;
  -webkit-animation-duration: 0.5s;
  animation-name: animarsuperior;
  animation-duration: 0.5s;
}


@keyframes animarsuperior {
  from {
    top: -300px;
    opacity: 0
  }

  to {
    top: 0;
    opacity: 1
  }
}

.per {
  background-color: rgb(165, 165, 165);
  opacity: .2;
}
</style>
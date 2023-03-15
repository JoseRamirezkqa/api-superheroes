<template>
  <div>
    <div ref="contenedor" class="grid 2xl:grid-cols-4 sm:grid-cols-2 lg:grid-cols-3  2xl:px-[0.625rem] pt-[0.625rem] 2xl:pt-[1.875rem] 2xl:mx-[3.125rem]">
      <card v-for="i, index in id" :key="i" :link="image[index]" :name="name[index]" :race="race[index]" :idn="id[index]"
        :to="`/${id[index]}`" :occupation="occupation[index]" :id="index"   
        class="animate__animated animate__zoomIn animate__slower" />
    </div>
    <div class="flex justify-center items-center 2xl:h-[6.25rem]">
      <button @click="previousPage" class="2xl:w-[9.375rem] 2xl:mt-[0.625rem] hover:bg-[#9F9C9C] duration-500 rounded-full 
        2xl:border-[0.156rem] border-black 2xl:h-[3.125rem] 2xl:mr-[0.625rem] transition ease-in-out delay-150 hover:scale-110
        h-[3.125rem] w-[6.25rem] my-[0.938rem] sm:w-[8rem] " v-if="pag">
        Previous
      </button>
      <button @click="nextPage" class=" 2xl:w-[9.375rem] 2xl:mt-[0.625rem] hover:bg-[#9F9C9C] duration-500 rounded-full 
        2xl:border-[0.156rem] border-black 2xl:h-[3.125rem] transition ease-in-out delay-150 hover:scale-110
        h-[3.125rem] w-[6.25rem] my-[0.938rem]  sm:w-[8rem] " v-if="pagFinal">
        Next
      </button>
    </div>
  </div>
</template>
<script>
import 'animate.css';
export default {
  name: "IndexPage",
  layout: "sexo",
  data() {
    return {
      url: `https://www.superheroapi.com/api.php/5924508177585115/`,
      data: [],
      image: [],
      name: [],
      race: [],
      id: [],
      occupation: [],
      inicio: 1,
      final: 12,
      pag: false,
      pagFinal: true
    }
  },
  methods: {
    nextPage() {
      this.inicio += 12
      this.final += 12
      this.data = [];
      this.image = [];
      this.name = [];
      this.race = [];
      this.id = [];
      this.occupation = [];
      this.pag = true;
      if (this.final >= 733) {
        this.pagFinal = false
      }
      this.create()
    },
    previousPage() {
      this.inicio -= 12
      this.final -= 12
      this.data = [];
      this.image = [];
      this.name = [];
      this.race = [];
      this.id = [];
      this.occupation = [];
      if (this.inicio == 1) {
        this.pag = false
      }
      this.create()
    },
    async create() {
      console.log(this.id)
      for (let i = this.inicio; i <= this.final; i++) {
        const response = await this.$axios.get(this.url + `${i}`)
        const data = response.data
        const { url } = data.image;
        this.image.push(url);
        const { name } = data
        this.name.push(name)
        const { race } = data.appearance
        this.race.push(race)
        const { id } = data
        this.id.push(id)
        const { occupation } = data.work
        this.occupation.push(occupation)
        if (this.$refs == 1) {
          console.log(this.refs)
        }
      }
    }
  },
  beforeMount() {
    this.create()
    },
}
</script>
<template>
  <div>
    <div ref="contenedor" class="grid sm:grid-cols-4 sm:px-[0.625rem] pt-[10px] sm:pt-[1.875rem] sm:mx-[3.125rem]">
      <card v-for="i, index in 12" :key="i" :link="image[i - 1]" :name="name[i - 1]" :race="race[i - 1]" :idn="id[i - 1]" :to="`/${id[i - 1]}`"
        :occupation="occupation[i - 1]" :id="index" class="animate__animated animate__zoomIn animate__slower"/>
    </div>
    <div class="flex justify-center items-center sm:h-[6.25rem]">
      <button @click="previousPage" class="sm:w-[9.375rem] sm:mt-[0.625rem] hover:bg-[#9F9C9C] duration-500 rounded-full 
      sm:border-[0.156rem] border-black sm:h-[3.125rem] sm:mr-[0.625rem] transition ease-in-out delay-150 hover:scale-110
      h-[3.125rem] w-[6.25rem] my-[0.938rem]" v-if="pag">
        Previous
      </button>
      <button @click="nextPage" class=" sm:w-[9.375rem] sm:mt-[0.625rem] hover:bg-[#9F9C9C] duration-500 rounded-full 
      sm:border-[0.156rem] border-black sm:h-[3.125rem] transition ease-in-out delay-150 hover:scale-110
      h-[3.125rem] w-[6.25rem] my-[0.938rem]    " v-if="pagFinal">
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
  async created() {
    console.log(this.$route)
    await this.create()
  }
}
</script>
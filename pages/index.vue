<template>
  <div>
    <div ref="contenedor" class="grid grid-cols-4 px-[10px] pt-[30px] mx-[50px]">
      <card v-for="i, index in 12" :key="i" :link="image[i - 1]" :name="name[i - 1]" :race="race[i - 1]" :idn="id[i - 1]" :to="`/${id[i - 1]}`"
        :occupation="occupation[i - 1]" :id="index"/>
    </div>
    <div class="flex justify-center items-center h-[100px]">
      <button @click="previousPage" class="w-[150px] mt-[10px] hover:bg-[#9F9C9C] duration-500 rounded-full 
                                            border border-[2.5px] border-black h-[50px] mr-[10px] transition ease-in-out delay-150 hover:scale-110" v-if="pag">
        Previous
      </button>
      <button @click="nextPage" class=" w-[150px] mt-[10px] hover:bg-[#9F9C9C] duration-500 rounded-full 
                                        border border-[2.5px] border-black h-[50px] transition ease-in-out delay-150 hover:scale-110" v-if="pagFinal">
        Next
      </button>
    </div>
  </div>
</template>
<script>

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
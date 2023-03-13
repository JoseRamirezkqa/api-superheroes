<template>
    <div >
        <div class="flex justify-center sm:pt-[3.125rem] pt-[0.625rem] ">
            <div class="border border-black justify-self-center shadow-slate-500 shadow-2xl sm:mb-[1.25rem] sm:w-[40%] sm:h-[37.5rem] 
                        grid sm:grid-cols-2 justify-items-center p-[1rem] sm:p-[5rem] w-[95%]">
                <img :src="urlImage" alt="" class="sm:w-[15.625rem] shadow-slate-500 shadow-lg w-[95%]">
                <div class="sm:px-[0.625rem] sm:py-[0.313rem] text-xl w-[95%] mt-[0.625rem]">
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
                    <powestats :combat="combat" :durability="durability"  :power="power" :speed="speed"
                        :strength="strength" :intelligence="intelligence"/>
                </div>
                <h1 class="sm:text-6xl text-4xl font-black sm:pt-[0.625rem]">Id: {{ id }} </h1>
                <div>
                    <nuxt-link class="bg-[rgb(251,71,71)] sm:w-[9.375rem] sm:mt-[0.625rem] hover:bg-[#D00F0F] duration-500 
                    rounded-full  sm:border-[0.156rem] border-black sm:h-[3.125rem] items-center flex  
                    justify-center transition ease-in-out delay-150 hover:scale-110 h-[3.125rem] w-[6.25rem] my-[0.938rem]"
                        to="/">
                        Volver
                    </nuxt-link>
                </div>
            </div>

        </div>

    </div>
</template>

<script>
export default {
    name: 'DetallePage',
    data() {
        return {
            url: `https://www.superheroapi.com/api.php/5924508177585115/`,
            id: '',
            name: '',
            urlImage: '',
            race: '',
            occupation: '',
            combat: '',
            durability: '',
            intelligence: '',
            power: '',
            speed: '',
            strength: '',
            firstAppearance: ''
        }
    },
    methods: {
        async create() {
            const response = await this.$axios.get(this.url + `${this.id}`)
            const data = response.data
            console.log(data)
            this.urlImage = data.image.url
            this.name = data.name
            this.race = data.appearance.race
            this.occupation = data.work.occupation
            this.combat = data.powerstats.combat
            this.durability = data.powerstats.durability
            this.intelligence = data.powerstats.intelligence
            this.power = data.powerstats.power
            this.speed = data.powerstats.speed
            this.strength = data.powerstats.strength
            this.firstAppearance = data.biography['first-appearance']
        }
    },
    async created() {
        console.log(this.$route)
        this.id = this.$route.params.id
        console.log(this.id)
        await this.create()
    }
}
</script>
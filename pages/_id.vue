<template>
    <div>
        <div class="flex justify-center pt-[50px]">
            <div class="border border-black justify-self-center shadow-slate-500 shadow-2xl mb-[20px] w-[40%] h-[600px] 
                        grid grid-cols-2 justify-items-center p-[80px]">
                <img :src="urlImage" alt="" class="w-[250px] shadow-slate-500 shadow-lg ">
                <div class="px-[10px] py-[5px] text-xl">
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
                    <powestats :combat="combat" :durability="durability"  :power="power" :speed="speed"
                        :strength="strength" :intelligence="intelligence"/>
                </div>
                <h1 class="text-6xl font-black pt-[10px]">Id: {{ id }} </h1>
                <div>
                    <nuxt-link class="bg-[#FB4747] w-[150px] mt-[20px] hover:bg-[#D00F0F] duration-500 
                                rounded-full border border-[2.5px] border-black h-[50px] items-center flex  
                                justify-center font-bold transition ease-in-out delay-150 hover:scale-110"
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
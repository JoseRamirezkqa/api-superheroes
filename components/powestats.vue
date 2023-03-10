<template>
    <div>
        <h1 class="font-black block mr-[5px]">powerstats: </h1>
        <div class="block px-[5px]">
            <h1 class="font-medium  inline-block mr-[5px]">· combat: </h1>
            <h1 class="font-normal inline-block">{{ combat }},</h1>
        </div>
        <div class="block px-[5px]">
            <h1 class="font-medium inline-block mr-[5px]">· durability: </h1>
            <h1 class="font-normal inline-block">{{ durability }},</h1>
        </div>
        <div class="block px-[5px]">
            <h1 class="font-medium inline-block mr-[5px]">· intelligence: </h1>
            <h1 class="font-normal inline-block">{{ intelligence }},</h1>
        </div>
        <div class="block px-[5px]">
            <h1 class="font-medium inline-block mr-[5px]">· power: </h1>
            <h1 class="font-normal inline-block">{{ power }},</h1>
        </div>
        <div class="block px-[5px]">
            <h1 class="font-medium inline-block mr-[5px]">· speed: </h1>
            <h1 class="font-normal inline-block">{{ speed }},</h1>
        </div>
        <div class="block  px-[5px]">
            <h1 class="font-medium inline-block mr-[5px]">· strength: </h1>
            <h1 class="font-normal inline-block">{{ strength }},</h1>

        </div>
    </div>
</template>
<script>
export default {
    props: {
        combat: String,
        durability: String,
        intelligence: String,
        power: String,
        speed: String,
        strength: String,
    }
}
</script>
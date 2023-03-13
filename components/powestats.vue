<template>
    <div>
        <h1 class="font-black block sm:mr-[0.313rem]">powerstats: </h1>
        <div class="block sm:px-[0.313rem]">
            <h1 class="font-medium  inline-block sm:mr-[0.313rem]">· combat: </h1>
            <h1 class="font-normal inline-block">{{ combat }},</h1>
        </div>
        <div class="block sm:px-[0.313rem]">
            <h1 class="font-medium inline-block sm:mr-[0.313rem]">· durability: </h1>
            <h1 class="font-normal inline-block">{{ durability }},</h1>
        </div>
        <div class="block sm:px-[0.313rem]">
            <h1 class="font-medium inline-block mr-[0.313rem]">· intelligence: </h1>
            <h1 class="font-normal inline-block">{{ intelligence }},</h1>
        </div>
        <div class="block sm:px-[0.313rem]">
            <h1 class="font-medium inline-block mr-[0.313rem]">· power: </h1>
            <h1 class="font-normal inline-block">{{ power }},</h1>
        </div>
        <div class="block sm:px-[0.313rem]">
            <h1 class="font-medium inline-block sm:mr-[0.313rem]">· speed: </h1>
            <h1 class="font-normal inline-block">{{ speed }},</h1>
        </div>
        <div class="block  sm:px-[0.313rem]">
            <h1 class="font-medium inline-block sm:mr-[0.313rem]">· strength: </h1>
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
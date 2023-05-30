<template>
    <div v-for="item in stuff.products.filter(
        function (i) { return i.id == productId })" class="w-full h-full">
        <div class="head flex flex-row items-center w-full">
            <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                Room in a rental unit hosted by {{ item.brand }}
            </h1>
            <div class="img w-[50px] h-[50px] ml-auto">
                <img class="float-right w-[50px] h-[50px] rounded-[50%]" :src="item.thumbnail" alt="">
            </div>
        </div>
        <div class="facility grid grid-cols-3 gap-[16px] w-full mt-[20px] border-b-[1px] pb-[20px] border-[#767676]">
            <div class="card01 w-full bg-white border-[1px] border-[#767676] rounded-[4px] h-[60px] shadow-lg
             flex flex-row items-center p-[10px] text-[16px] leading-[19px] font-[300] text-[#484848]">
                Facility 01
            </div>
            <div class="card02 w-full bg-white border-[1px] border-[#767676] rounded-[4px] h-[60px] shadow-lg
             flex flex-row items-center p-[10px] text-[16px] leading-[19px] font-[300] text-[#484848]">
                Facility 02
            </div>
            <div class="card03 w-full bg-white border-[1px] border-[#767676] rounded-[4px] h-[60px] shadow-lg
             flex flex-row items-center p-[10px] text-[16px] leading-[19px] font-[300] text-[#484848]">
                Facility 03
            </div>
        </div>
        <div class="service w-full flex flex-col items-start mt-[20px]">
            <div class="serv01 w-full">
                <h1 class="font-[700] text-[19px] leading-[24px] text-[#484848] mb-[8px]">
                    Service 01
                </h1>
                <p class="font-[300] text-[16px] leading-[19px] text-[#767676]">
                    desc 01
                </p>
            </div>
            <div class="serv02 w-full mt-[20px] mb-[20px]">
                <h1 class="font-[700] text-[19px] leading-[24px] text-[#484848] mb-[8px]">
                    Service 02
                </h1>
                <p class="font-[300] text-[16px] leading-[19px] text-[#767676]">
                    desc 02
                </p>
            </div>
            <div class="serv03 w-full">
                <h1 class="font-[700] text-[19px] leading-[24px] text-[#484848] mb-[8px]">
                    Service 03
                </h1>
                <p class="font-[300] text-[16px] leading-[19px] text-[#767676]">
                    desc 03
                </p>
            </div>
        </div>
    </div>
</template>

<script setup>
const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products')
</script>

<style lang="scss" scoped></style>
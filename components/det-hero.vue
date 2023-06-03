<template>
    <div v-for="item in stuff.products.filter(
        function (i) { return i.id == productId })" class="w-full mt-[20px]">
        <div class="texts w-full flex flex-col items-start">
            <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                {{ item.title }}
            </h1>
            <p class="font-[300] text-[16px] leading-[19px] text-[#484848] mb-[8px] mt-[5px]">
                {{ item.category }}
            </p>
            <div class="rating flex flex-row items-center mb-[24px]">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-3 h-3 mr-[5px]">
                    <path fill-rule="evenodd"
                        d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z"
                        clip-rule="evenodd" />
                </svg>
                <p>{{ item.rating }}</p>
            </div>
        </div>

        <div class="det-img grid grid-cols-2 gap-[16px] w-full h-[322.22px] rounded-[10px]">
            <div class="beegimg w-full h-full bg-black rounded-[10px]">
                <img class="opacity-100 hover:opacity-80 transition ease-in-out delay-[30ms]
                            h-[322.22px] w-full object-cover rounded-tl-[10px] rounded-bl-[10px]" :src="item.thumbnail" alt="">
            </div>

            <div class="miniImg grid grid-cols-2 gap-[16px] w-full h-full">
                <div class="w-full h-[153.11px] bg-black">
                    <img :src="item.images[0]"
                        class="text-whtie object-cover opacity-100 hover:opacity-80 transition ease-in-out delay-[30ms] h-full w-full" alt="Image Unavailable">
                </div>
                <div class="w-full h-[153.11px] bg-black rounded-tr-[10px]">
                    <img :src="item.images[1]"
                        class="text-whtie object-cover opacity-100 hover:opacity-80 transition ease-in-out delay-[30ms] h-full w-full rounded-tr-[10px]"
                        alt="Image Unavailable">
                </div>
                <div class="w-full h-[153.11px] bg-black">
                    <img :src="item.images[2]"
                        class="text-whtie object-cover opacity-100 hover:opacity-80 transition ease-in-out delay-[30ms] h-full w-full" alt="Image Unavailable">
                </div>
                <div class="w-full h-[153.11px] bg-black rounded-br-[10px]">
                    <img :src="item.images[3]"
                        class="text-whtie object-cover opacity-100 hover:opacity-80 transition ease-in-out delay-[30ms] h-full w-full rounded-br-[10px]"
                        alt="Image Unavailable">
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products?limit=0')
</script>

<script>
export default{
    data(){
        return{

        }
    }
}
</script>

<style lang="scss" scoped></style>

<!--  -->

<!-- <template>
    <div>
        {{ productId }}
        <div v-for="item in stuff.products.filter(
            function (i) { return i.id == productId })">
            <p>
                {{ item.id }}
                {{ item.title }}
            </p>
        </div>
    </div>
</template>

<script setup>
const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products')
</script>

<style lang="scss" scoped></style> -->
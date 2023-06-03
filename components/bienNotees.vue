<template>
    <div id="exp" class="daFont w-[1208px] h-[469px] left-[80px] mt-[88px]">
        <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
            Expériences très bien notées
        </h1>
        <p class="w-[577px] mt-[8px] font-[300] text-[16px] leading-[19px] text-[#484848]">
            Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
        </p>
        <div class="cardHolder w-full grid grid-cols-6 gap-[16px] mt-[24px]">
            <div class="card w-[188px] h-[240px] rounded-[4px]" v-for="item in data.products" :key="item.id">
                <div class="cardContent flex flex-col items-start">
                    <NuxtLink to="#">
                        <img :src="item.thumbnail"
                            class="h-[240px] object-cover hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            alt="">
                    </NuxtLink>
                    <p class="font-[700] text-[10px] leading-[12px] text-[#767676] uppercase mt-[8px]">
                        {{ item.category }}
                    </p>
                    <p class="font-[700] text-[16px] leading-[19px] text-[#484848] mt-[4px]">
                        {{ item.title }}
                    </p>
                    <p class="font-[300] text-[14px] leading-[21px] mt-[8px] text-[#484848] w-[180px]">
                        ${{ item.price }}
                    </p>
                    <div class="rating flex flex-row items-center mt-[5px]">
                        <p class="font-[300] text-[12px] leading-[14px] text-[#008489]">
                            {{ item.rating }}
                        </p>
                        <img src="/Star.png" class="h-[8px] w-[8px] ml-[4px]" alt="">
                    </div>
                    <div class="w-full mt-[5px]">
                        <button class="hover:border-[#FF5A5F] hover:text-[#FF5A5F] hover:stroke-[#FF5A5F] hover:bg-white
                        transition ease-in-out delay-[30ms]
                        w-full border-[1px] border-[#FF5A5F] rounded-[4px] text-white stroke-white bg-[#FF5A5F]
                        flex flex-row items-center justify-center">
                            <p class="text-[12px] leading-[14px]">
                                Add to cart
                            </p>
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                class="w-5 h-5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                            </svg>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: data } = await useFetch('https://dummyjson.com/products?limit=6&skip=14')
</script>

<script>
import airbnb from '/json/airbnb.json'
export default {
    data() {
        return {

        }
    }
}

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.daFont {
    font-family: 'Roboto', sans-serif;
}
</style>
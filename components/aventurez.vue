<template>
    <div id="aventurez" class="daFont not-italic w-[1208px] h-[469px] mt-[88px]">
        <h1 class=" w-[342px] h-[28px] mb-[8px] not-italic font-[700] text-[24px] leading-[28px] text-[#484848]">
            Découvrez les aventures Airbnb
        </h1>
        <p class=" w-[580px] h-[38px] mb-[24px] font-[300] text-[16px] leading-[19px] text-[#484848]">
            Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
        </p>
        <div class="cardHolderCase  grid grid-cols-6 gap-[16px] justify-start w-[1208px] h-[371px] top-[20.9%]">
            <div v-for="stuff in item.products" class="cards flex flex-col items-start justify-start rounded-[4px]">
                <div class="cardContent rounded-[4px]">
                    <NuxtLink :to="'details/' + stuff.id">
                        <img class="h-[240px] rounded-[4px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            :src="stuff.thumbnail" alt="">
                    </NuxtLink>
                    <p class="mt-[8px] mb-[4px] font-[700] text-[10px] leading-[12px] uppercase text-[#767676]">
                        {{ stuff.category }}
                    </p>
                    <h1 class="w-[188px] font-[700] text-[13px] leading-[13px] text-[#484848]">
                        {{ stuff.title }}
                    </h1>
                    <p class="mt-[8px] w-[188px] font-[300] text-[14px] leading-[21px] text-[#484848]">
                        ${{ stuff.price }}
                    </p>
                    <div class="rating mt-[5px] w-[30px] flex flex-row items-center">
                        <p class="font-700 text-[12px] leading-[14px] text-[#008489]">
                            {{ stuff.rating }}
                        </p>
                        <img src="/Star.png" class=" ml-[5px] h-[8px] w-[8px]">
                    </div>
                    <div class="w-full h-[28px] mt-[5px]">
                        <button class="w-full h-full">
                            <div class="w-full h-full
                            flex flex-row items-center justify-center
                            text-white stroke-white bg-[#FF5A5F] border-[1px] border-[#FF5A5F]
                            hover:text-[#FF5A5F] hover:stroke-[#FF5A5F] hover:bg-white rounded-[4px]
                            transition ease-in-out delay-[30ms]">
                                <h1 class="text-[14px] leading-[18px] font-[300]">
                                    Add to cart
                                </h1>
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                    class="w-5 h-5">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                                </svg>
                            </div>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: item } = await useFetch('https://dummyjson.com/products?limit=6')
</script>

<script>
import airbnb from '/json/airbnb.json'
export default {
    data() {
        return {
            data: airbnb.aventurez
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
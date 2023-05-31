<template>
    <div id="aventurez"
    class="daFont not-italic absolute w-[1208px] h-[469px] left-[80px] right-[80px] top-[1540px]">
        <h1
            class="absolute w-[342px] h-[28px] left-0 top-0 not-italic font-[700] text-[24px] leading-[28px] text-[#484848]">
            Découvrez les aventures Airbnb
        </h1>
        <p class="absolute w-[580px] h-[38px] left-0 top-[36px] font-[300] text-[16px] leading-[19px] text-[#484848]">
            Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
        </p>
        <div class="cardHolderCase absolute grid grid-cols-6 gap-[16px] justify-start w-[1208px] h-[371px] top-[20.9%]">
            <div v-for="stuff in item.products" class="cards flex flex-col items-start justify-start rounded-[4px]">
                <div class="cardContent rounded-[4px]">
                    <NuxtLink :to="'details/'+ stuff.id">
                        <img class="h-[240px] rounded-[4px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            :src="stuff.thumbnail" alt="">
                    </NuxtLink>
                    <p class="absolute top-[248px] font-[700] text-[10px] leading-[12px] uppercase text-[#767676]">
                        {{ stuff.category }}
                    </p>
                    <h1 class="absolute top-[264px] w-[188px] font-[700] text-[13px] leading-[13px] text-[#484848]">
                        {{ stuff.title }}
                    </h1>
                    <p class="absolute top-[280px] w-[188px] font-[300] text-[14px] leading-[21px] text-[#484848]">
                        ${{ stuff.price }}
                    </p>
                    <div class="rating mt-[75px] w-[30px] flex flex-row items-center">
                        <p class="font-700 text-[12px] leading-[14px] text-[#008489]">
                            {{ stuff.rating }}
                        </p>
                        <img src="/Star.png" class=" ml-[5px] h-[8px] w-[8px]">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const { data:item } = await useFetch('https://dummyjson.com/products?limit=6')
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
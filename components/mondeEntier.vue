<template>
    <div id="loge" class="daFont md:w-[1208px] w-full md:mt-[88px] mt-[20px]">
        <div class="flex md:flex-row flex-col md:items-center items-start">
            <div class="div flex flex-col items-start">
                <h1 class="md:ml-0 ml-[5px] font-[700] text-[24px] leading-[28px] text-[#484848]">
                    Logements dans le monde entier
                </h1>
                <p
                    class="md:w-[577px] w-full md:ml-0 ml-[5px] mt-[8px] font-[300] text-[16px] leading-[19px] text-[#484848]">
                    Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
                </p>
            </div>
            <NuxtLink to="seeAll"
                class="border-[1px] border-[#484848] rounded-[20px] md:ml-auto ml-[5px] md:mt-0 mt-[10px] p-[10px]
                                            hover:text-black hover:stroke-black text-[#484848] stroke-[#484848] hover:border-black transition ease-in-out delay-[30ms]">
                <button class=" w-full flex flex-row items-center text-center">
                    <h1 class="
                                                        font-[700] text-[16px] leading-[19px]">
                        See all products
                    </h1>
                </button>
            </NuxtLink>
        </div>

        <div class="w-full h-full md:block flex-row items-center">
            <div class="cardHolder md:grid md:grid-cols-4 flex items-center gap-[16px] md:w-[1208px] w-full md:pl-0 pl-[10px] overflow-x-scroll md:pr-0 pr-[10px] md:mt-[24px] mt-[10px]">
                <div v-for="item in data.products" :key="item.id" class="cards w-[290px]">
                    <div class="cardContent flex flex-col items-start w-[290px] relative">
                        <Swiper
                            class="groupSwiper w-[290px] h-[200px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[30ms]"
                            :modules="[SwiperAutoplay, SwiperEffectCreative, SwiperPagination, SwiperNavigation]"
                            :slides-per-view="1" :loop="false" :effect="'creative'" :navigation="true" :hashNavigation="{
                                watchState: true,
                            }" :pagination="{ clickable: true }" :creative-effect="{
    prev: {
        shadow: false,
        translate: ['-100%', 0, -1],
    },
    next: {
        translate: ['100%', 0, 0],
    },
}">
                            <SwiperSlide v-for="image in item.images" class="w-[290px] h-[200px]">
                                <NuxtLink :to="'/details/' + item.id" class="w-[290px] h-[200px]">
                                    <img :src="image" alt=""
                                        class="w-[290px] h-[200px] object-cover duration-1000 rounded-[4px]">
                                </NuxtLink>
                            </SwiperSlide>
                        </Swiper>

                        <!-- <button id="left" @click="left"
                        class="hover:bg-white hover:stroke-[#FF5A5F] transition ease-in-out delay-[30ms] stroke-white w-[30px] h-[30px] border-[1px] border-[#FF5A5F] absolute top-[85px] left-[7px] rounded-[50%] bg-[#FF5A5F]">
                        <div class="w-full h-full flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                class="w-3 h-3">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
                            </svg>
                        </div>
                    </button>
                    <button id="right" @click="right"
                        class="hover:bg-white hover:stroke-[#FF5A5F] stroke-white transition ease-in-out delay-[30ms] z-[100] w-[30px] h-[30px] border-[1px] border-[#FF5A5F] absolute top-[85px] right-[7px] rounded-[50%] bg-[#FF5A5F]">
                        <div class="w-full h-full flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                class="w-3 h-3">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
                            </svg>

                        </div>
                    </button> -->

                        <div class="texts flex flex-col items-start w-full">
                            <div class="txt01 grid grid-cols-5 justify-center mt-[8px] w-full">
                                <NuxtLink :to="'/category/' + item.category" class="w-full h-full col-span-2">
                                    <button
                                        class="w-full h-[32px] border-[1px] border-black rounded-[4px] box-border hover:border-[#FF5A5F] hover:text-[#FF5A5F] transition ease-in-out delay-[30ms]">
                                        <div class=" w-full h-[30px] flex flex-row items-center justify-center">
                                            <p class="text-center font-[700] text-[10px] leading-[12px] uppercase">
                                                {{ item.category }}
                                            </p>
                                        </div>
                                    </button>
                                </NuxtLink>

                                <div class="col-span-2 flex flex-row items-center w-full h-full ml-[13px]">
                                    <p class=" font-[400] text-[12px] leading-[14px] text-[#767676]">
                                        {{ item.title }}
                                    </p>
                                </div>

                                <div class="flex flex-row items-center justify-end">
                                    <img src="/gStar.png" class="h-[8px] w-[8px] mr-[3px]" alt="">
                                    <p class="font-[500p] text-[12px] leading-[14px] text-right text-[#484848]">
                                        {{ item.rating }}
                                    </p>
                                </div>

                            </div>
                            <p class="w-full font-[400] text-[14px] leading-[21px] text-[#484848] mt-[8px]">
                                ${{ item.price }}
                            </p>

                        </div>
                    </div>
                </div>

            </div>
        </div>

    </div>
</template>

<script setup>
const { data: data } = await useFetch('https://dummyjson.com/products?limit=8&skip=6')
</script>

<script>
import airbnb from '/json/airbnb.json'
export default {
    data() {
        return {
        }
    }
    ,
    methods: {
        left() {

        }
    }
}

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.daFont {
    font-family: 'Roboto', sans-serif;
}

.cardHolder::-webkit-scrollbar {
    height: 5px;
}

.cardHolder::-webkit-scrollbar-track {
    background: transparent;
}

.cardHolder::-webkit-scrollbar-thumb {
    background: #FF5A5F;
    border-radius: 4px;
}
</style>
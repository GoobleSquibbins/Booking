<template>
    <div id="exp" class="daFont md:w-[1208px] w-full h-[469px] left-[80px] md:mt-[88px] mt-[25px]">
        <div class="header flex md:flex-row flex-col items-start w-full">
            <div class="texts flex flex-col">
                <h1 class="font-[700] text-[24px] md:ml-0 ml-[5px] leading-[28px] text-[#484848]">
                    Expériences très bien notées
                </h1>
                <p class="md:w-[577px] w-full mt-[8px] font-[300] md:ml-0 ml-[5px] text-[16px] leading-[19px] text-[#484848]">
                    Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
                </p>
            </div>
            <NuxtLink to="seeAll"
                class="border-[1px] border-[#484848] rounded-[20px] md:ml-auto ml-[5px] md:mt-0 mt-[10px] p-[10px]
                    hover:text-black hover:stroke-black text-[#484848] stroke-[#484848] hover:border-black transition ease-in-out delay-[30ms]">
                <button class="
                            w-full
                            flex flex-row items-center text-center">
                    <h1 class="
                                font-[700] text-[16px] leading-[19px]">
                        See all products
                    </h1>
                </button>
            </NuxtLink>
        </div>

        <div class="cardHolder w-full md:grid flex md:grid-cols-6 items-center md:pl-0 pl-[5px] md:pr-0 pr-[5px] gap-[16px] md:mt-[24px] mt-[10px] md:overflow-visible overflow-x-scroll">
            <div class="card w-[188px] md:h-[240px] h-full rounded-[4px]" v-for="item in data.products" :key="item.id">
                <div class="cardContent flex flex-col items-start">

                    <Swiper class="groupSwiper w-[188px] h-[240px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[30ms]"
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
                        <SwiperSlide v-for="image in item.images" class="w-[188px] h-[240px]">
                            <NuxtLink :to="'/details/' + item.id" class="w-[188px] h-[240px]">
                                <img :src="image" alt=""
                                    class="w-[188px] h-[240px] object-cover duration-1000 rounded-[4px] ">
                            </NuxtLink>
                        </SwiperSlide>
                    </Swiper>

                    <!-- <NuxtLink to="#">
                        <img :src="item.thumbnail"
                            class="h-[240px] object-cover hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            alt="">
                    </NuxtLink> -->

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
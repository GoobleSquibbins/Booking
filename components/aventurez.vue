<template>
    <div id="aventurez"
        class="daFont flex-col md:items-start items-center not-italic md:w-[1208px] w-full md:h-[469px] h-full md:mt-[88px] mt-[30px]">
        <div class="headder w-full flex md:flex-row flex-col md:items-center items-start md:mb-0 mb-[10px]">
            <div class="textes flex flex-col items-start md:w-[580px] w-full">
                <h1 class="md:ml-0 ml-[5px] mb-[8px] not-italic font-[700] text-[24px] leading-[28px] text-[#484848]">
                    Découvrez les aventures Airbnb
                </h1>
                <p
                    class="md:w-[580px] w-full h-[38px] md:mb-[24px] mb-[20px] md:ml-0 ml-[5px] font-[300] text-[16px] leading-[19px] text-[#484848]">
                    Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
                </p>
            </div>

            <NuxtLink to="/seeAll"
                class="border-[1px] border-[#484848] rounded-[20px] md:ml-auto ml-[5px] p-[10px]
                        hover:text-black hover:stroke-black text-[#484848] stroke-[#484848] hover:border-black transition ease-in-out delay-[30ms]">
                <button class="
                                w-full
                                flex flex-row items-center text-center ">
                    <h1 class="
                                    font-[700] text-[16px] leading-[19px]">
                        See all products
                    </h1>
                </button>
            </NuxtLink>
        </div>

        <div class="w-full flex-col items-center justify-center">
            <div
                class="cardHolder md:justify-start cardHolderCase md:grid md:grid-cols-6 flex items-center md:overflow-hidden overflow-x-scroll md:gap-[16px] gap-[10px] md:w-[1208px] w-full md:h-[371px] h-full md:pl-0 pl-[10px] md:pr-0 pr-[10px]">
                <div v-for="stuff in item.products" class="cards flex flex-col md:items-start items-center justify-start rounded-[4px]">
                    <div class="cardContent rounded-[4px]">
                        <Swiper class="groupSwiper w-[188px] h-[240px] hover:shadow-2xl hover:shadow-[#335b8f85]"
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
                            <SwiperSlide v-for="image in stuff.images" class=" w-full h-[240px]">
                                <NuxtLink :to="'/details/' + stuff.id" class=" w-full h-[240px]">
                                    <img :src="image" alt=""
                                        class="md:w-[188px] w-full h-[240px] object-cover duration-1000 rounded-[4px]">
                                </NuxtLink>
                            </SwiperSlide>
                        </Swiper>

                        <!-- <NuxtLink :to="'details/' + stuff.id">
                        <img class="h-[240px] object-cover rounded-[4px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            :src="stuff.thumbnail" alt="">
                    </NuxtLink> -->

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
<template>
    <div class="daFont md:w-[1208px] w-full md:mt-[88px] mt-[50px]">
        <div class="header w-full flex md:flex-row flex-col md:items-center items-start">
            <div class="texte flex flex-col">
                <h1 class="md:ml-0 ml-[5px] font-[700] text-[24px] leading-[28px] text-[#484848]">
                    Destinations Airbnb Plus à la Une
                </h1>
                <p class="md:w-[577px] w-full md:ml-0 ml-[5px] mt-[8px] font-[300] text-[16px] leading-[19px] text-[#484848]">
                    Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
                </p>
            </div>
            <NuxtLink to="seeAll"
                class="border-[1px] border-[#484848] rounded-[20px] ml:ml-auto ml-[5px] md:mt-0 mt-[10px] p-[10px]
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

        <div class="cardHolder md:overflow-x-hidden overflow-x-scroll w-full mt-[32px] md:grid flex md:grid-cols-3 items-center md:pl-0 pl-[5px] md:pr-0 pr-[5px] gap-[16px]">
            <div class="card w-[391px] h-[294px]" v-for="item in data.products" :key="item.id">
                <div class="cardContent flex flex-col w-full h-full item-start">

                    <Swiper
                        class="groupSwiper w-full h-[239px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[30ms]"
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
                        <SwiperSlide v-for="image in item.images" class="w-full h-[239px]">
                            <NuxtLink :to="'/details/' + item.id" class="w-full h-[239px]">
                                <img :src="image" alt="" class="w-full h-[239px] object-cover duration-1000 rounded-[4px]">
                            </NuxtLink>
                        </SwiperSlide>
                    </Swiper>

                    <!-- <NuxtLink to="#">
                        <div class="img w-full h-[239px] rounded-[12px] flex flex-row items-center justify-center hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            v-bind:style="{ backgroundImage: 'url(' + item.thumbnail + ')' }">
                            <svg class="logoo transition ease-in-out delay-[30ms]" width="50" height="54"
                                viewBox="0 0 50 54" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M24.9594 40.7286C22.0014 37.0166 20.2614 33.7628 19.6814 30.9788C19.1014 28.7168 19.3334 26.9188 20.3194 25.5848C21.3634 24.0188 22.9294 23.2648 24.9594 23.2648C26.9894 23.2648 28.5554 24.0188 29.5994 25.5848C30.5854 26.9188 30.8174 28.7168 30.2374 30.9788C29.5994 33.8208 27.8594 37.0688 24.9594 40.7286ZM45.967 43.2226C45.561 45.9486 43.705 48.2106 41.153 49.3126C36.223 51.4586 31.3452 48.0366 27.1692 43.3966C34.077 34.7488 35.353 28.0208 32.3892 23.665C30.6492 21.171 28.1552 19.953 24.9594 19.953C18.5214 19.953 14.9776 25.405 16.3696 31.7328C17.1816 35.1548 19.3276 39.0466 22.7496 43.3966C20.6036 45.7746 18.5736 47.4566 16.7756 48.5006C15.3836 49.2546 14.0496 49.7186 12.7736 49.8346C6.91562 50.7046 2.32782 45.0206 4.41582 39.1568C4.70582 38.4028 5.28582 37.0108 6.27182 34.8648L6.32982 34.7488C9.51982 27.783 13.4116 19.895 17.8776 11.1312L17.9936 10.8412L19.2696 8.40521C20.2556 6.60721 20.6616 5.79521 22.2276 4.80921C22.9816 4.34521 23.9096 4.11321 24.9536 4.11321C27.0416 4.11321 28.6656 5.33121 29.3616 6.31721C29.7096 6.83921 30.1156 7.53521 30.6376 8.40521L31.8556 10.7832L32.0296 11.1312C36.4956 19.895 40.3874 27.783 43.5774 34.7488L43.6354 34.8068L44.7954 37.4748L45.4914 39.1568C46.025 40.4966 46.141 41.8306 45.967 43.2226ZM48.635 37.9968C48.229 36.7208 47.533 35.2128 46.663 33.4148V33.3568C42.545 24.593 38.7112 16.705 35.0572 9.62321L34.8252 9.27521C32.2152 3.93921 30.3592 0.743408 24.9594 0.743408C19.6234 0.743408 17.3556 4.45541 15.0356 9.27521L14.8616 9.62321C11.2076 16.705 7.37382 24.593 3.25582 33.3568V33.4728L2.03782 36.1408C1.57382 37.2428 1.34182 37.8228 1.28382 37.9968C-1.67418 46.1226 4.41582 53.2566 11.7876 53.2566C11.8456 53.2566 12.0776 53.2566 12.3676 53.1986H13.1796C17.0076 52.7346 20.9574 50.2986 24.9594 45.9428C28.9614 50.2928 32.9112 52.7346 36.7392 53.1986H37.5512C37.8412 53.2566 38.0732 53.2566 38.1312 53.2566C45.503 53.2624 51.593 46.1226 48.635 37.9968Z" />
                            </svg>
                        </div>
                    </NuxtLink> -->

                    <div class="texts flex flex-col items-start w-full mt-[10px]">
                        <div class="row01 grid grid-cols-5 gap-[10px] w-full">
                            <div class="w-full h-[28px] col-span-2 flex flex-row items-center justify-center ">
                                <NuxtLink :to="'/category/' + item.category" class="w-full h-full">
                                    <button
                                        class="w-full h-full border-[1px] rounded-[4px] border-black text-[#484848] hover:border-[#FF5A5F] hover:text-[#FF5A5F] transition ease-in-out delay-[30ms]">
                                        <div class="flex flex-row items-center justify-center
                                                w-full h-full rounded-[4px] ">
                                            <p class="font-[700] text-[10px] leading-[12px] uppercase">
                                                {{ item.category }}
                                            </p>
                                        </div>
                                    </button>
                                </NuxtLink>


                            </div>
                            <div class="col-span-2 text-[#767676]">
                                <div class="w-full h-full flex flex-row items-center justify-start">
                                    <p class=" font-[400] text-[12px] leading-[14px] text-[#767676]">
                                        {{ item.title }}
                                    </p>
                                </div>
                            </div>
                            <div class="rating flex flex-row items-center justify-end">
                                <img src="/gStar.png" class="h-[8px] w-[8px] mr-[3px]" alt="">
                                <p class="font-[500p] text-[12px] leading-[14px] text-right text-[#484848]">
                                    {{ item.rating }}
                                </p>
                            </div>
                        </div>

                        <div
                            class="row02 flex flex-col items-start w-full font-[400] text-[14px] leading-[21px] text-[#484848] mt-[8px]">
                            <div class="w-full h-full flex flex-row items-center justify-start">
                                <p class="text-[20px] mb-[8px]">
                                    ${{ item.price }}
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: data } = await useFetch('https://dummyjson.com/products?limit=3&skip=20')
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

.logoo {
    fill: white;
}

.img:hover>.logoo {
    fill: #FF5A5F;
}
</style>
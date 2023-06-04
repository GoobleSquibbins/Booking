<template>
    <div id="loge" class="daFont w-[1208px] mt-[88px]">
        <div class="flex flex-row items-center">
            <div class="div flex flex-col items-start">
                <h1 class=" font-[700] text-[24px] leading-[28px] text-[#484848]">
                    Logements dans le monde entier
                </h1>
                <p class="w-[577px] mt-[8px] font-[300] text-[16px] leading-[19px] text-[#484848]">
                    Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
                </p>
            </div>
            <NuxtLink to="seeAll" class="border-[1px] border-[#484848] rounded-[20px] ml-auto p-[10px]
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


        <div class="cardHolder grid grid-cols-4 gap-[16px]  w-[1208px] mt-[24px]">
            <div v-for="item in data.products" :key="item.id" class="cards w-[290px]">
                <div class="cardContent flex flex-col items-start w-[290px]">
                    <NuxtLink to="#">
                        <img class="object-cover w-[290px] h-[200px] rounded-[4px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]"
                            :src="item.thumbnail" alt="">
                    </NuxtLink>
                    <div class="texts flex flex-col items-start w-full">
                        <div class="txt01 grid grid-cols-5 justify-center mt-[8px] w-full">
                            <div class="col-span-2 border-[1px] border-black rounded-[2px] box-border w-full h-[30px] flex flex-row items-center justify-center">
                                <p class="text-center font-[700] text-[10px] leading-[12px] uppercase">
                                    {{ item.category }}
                                </p>
                            </div>
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

}

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.daFont {
    font-family: 'Roboto', sans-serif;
}
</style>
<template>
    <div class="daFont absolute w-[1208px] h-[400px] top-[3383px] left-[80px]">
        <h1 class="top-0 left-0 font-[700] text-[24px] leading-[28px] text-[#484848]">
            Destinations Airbnb Plus à la Une
        </h1>
        <p class="w-[577px] mt-[8px] font-[300] text-[16px] leading-[19px] text-[#484848]">
            Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
        </p>
        <div class="cardHolder w-full mt-[32px] grid grid-cols-3 gap-[16px]">
            <div class="card w-[391px] h-[294px]" v-for="item in data" :key="item.id">
                <div class="cardContent flex flex-col w-full h-full item-start">
                    <div class="img w-full h-[239px] rounded-[12px] flex flex-row items-center justify-center" v-bind:style="{ backgroundImage: 'url(' + item.imgg + ')' }">
                        <img src="/VectorBeeg.png" height="52.51px" width="48.88px" alt="">
                    </div>
                    <p class="mt-[10px] font-[700] text-[12px] leading-[14px] text-[#914669] uppercase">
                        Plus de 200 séjours vérifiés 
                    </p>
                    <p class="font-[400] text-[14px] leading-[21px] text-[#484848] mt-[10px]">
                        À partir de {{item.price}}€/personne - {{item.duration}} jours
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import airbnb from '/json/airbnb.json'
export default {
    data() {
        return {
            data: airbnb.bnbPlus
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
<template>
    <div class="daFont absolute w-[1208px] h-[469px] left-[80px] top-[2826px]">
        <h1 class="top-0 left-0 font-[700] text-[24px] leading-[28px] text-[#484848]">
            Expériences très bien notées
        </h1>
        <p class="w-[577px] mt-[8px] font-[300] text-[16px] leading-[19px] text-[#484848]">
            Voyages de plusieurs jours organisés par des experts locaux avec activités, repas et logements compris
        </p>
        <div class="cardHolder w-full grid grid-cols-6 gap-[16px] mt-[24px]">
            <div class="card w-[188px] h-[240px] rounded-[4px]" v-for="item in data" :key="item.id">
                <div class="cardContent flex flex-col items-start">
                    <img :src="item.imgg" class="h-[240px] hover:shadow-2xl hover:shadow-[#335b8f85] transition ease-in-out delay-[50ms]" alt="">
                    <p class="font-[700] text-[10px] leading-[12px] text-[#767676] uppercase mt-[8px]">
                        {{ item.location }}
                    </p>
                    <p class="font-[700] text-[16px] leading-[19px] text-[#484848] mt-[4px]">
                        {{ item.desc }}
                    </p>
                    <p class="font-[300] text-[14px] leading-[21px] mt-[8px] text-[#484848] w-[180px]">
                        À partir de {{item.price}}€/personne - {{item.duration}} jours
                    </p>
                    <div class="rating flex flex-row items-center mt-[5px]">
                        <p class="font-[700] text-[12px] leading-[14px] text-[#008489]">
                            {{ item.rating }}
                        </p>
                        <img src="/Star.png" class="h-[8px] w-[8px] ml-[4px]" alt="">
                    </div>
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
            data: airbnb.bienNotees
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
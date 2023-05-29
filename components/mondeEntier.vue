<template>
    <div class="daFont absolute w-[1208px] h-[641px] top-[2097px] left-[80px]">
        <h1 class="absolute font-[700] text-[24px] leading-[28px] text-[#484848] top-0 left-0">
            Logements dans le monde entier
        </h1>
        <div class="cardHolder grid grid-cols-4 gap-[16px] absolute w-[1208px] h-[562px] top-[79px]">
            <div v-for="item in data" :key="item.id" class="cards w-[290px] h-[265px]">
                <div class="cardContent flex flex-col items-start w-[290px] h-[265px]">
                    <img class="object-cover w-[290px] h-[200px] rounded-[4px]" :src="item.imgg" alt="">
                    <div class="texts flex flex-col items-start w-full">
                        <div class="txt01 flex flex-row items-center mt-[8px]">
                            <button
                                class="border-[1px] border-solid border-black rounded-[2px] box-border w-[74px] h-[28px]">
                                <p class="text-center font-[700] text-[10px] leading-[12px] text-[#484848] uppercase">
                                    {{ item.host }}
                                </p>
                            </button>
                            <p class="ml-[13px] font-[400] text-[12px] leading-[14px] text-[#767676] w-[159px]">
                                {{ item.location }}
                            </p>
                            <img src="/gStar.png" class="h-[8px] w-[8px] ml-[8px]" alt="">
                            <p class="ml-[4px] font-[500p] text-[12px] leading-[14px] text-right text-[#484848]">
                                {{ item.rating }}
                            </p>
                        </div>
                        <p class="w-full fomt-[400] text-[14px] leading-[21px] text-[#484848] mt-[8px]">
                            À partir de {{ item.price }}€/personne - {{ item.duration }} jours
                        </p>
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
            data: airbnb.all
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
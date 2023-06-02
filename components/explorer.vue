<template>
    <div class="daFont flex flex-col items-start w-[1208px] mt-[88px]">
        <h1 class="w-[181px] h-[28px] not-italic font-[700] text-[24px] leading-[28px] text-[#484848] mb-[24px]">
            Explorer Airbnb
        </h1>
        <div class="grid grid-cols-3 gap-[16px] justify-center w-full">
            <div class="miniCard01 miniCard w-full">
                <NuxtLink>
                    <button @click="aventurez"
                        class="bg_card w-full flex flex-row items-center bg-white rounded-[12px] transition ease-in-out delay-[30ms]">
                        <img class=" rounded-tl-[12px] rounded-bl-[12px] w-[121px] left-0 top-0 bottom-0"
                            src="/Rectangle4.png" alt="">
                        <h1
                            class="logements daFont ml-[24px] w-[88px] h-[19px] left-[145px] font-[600] text-[16px] leading-[19px]">
                            Aventures
                        </h1>
                    </button>
                </NuxtLink>
            </div>
            <div class="miniCard02 miniCard  left-[33.75%] right-[33.75%] top-[37.96%] bottom-[0%]">
                <NuxtLink>
                    <button @click="loge"
                        class="bg_card w-full flex flex-row items-center bg-white rounded-[12px] transition ease-in-out delay-[30ms]">
                        <img class=" rounded-tl-[12px] rounded-bl-[12px] w-[121px] left-0 top-0 bottom-0"
                            src="/Rectanglehrzn.png" alt="">
                        <h1
                            class="logements daFont ml-[24px] w-[88px] h-[19px] left-[145px] font-[600] text-[16px] leading-[19px]">
                            Logements
                        </h1>
                    </button>
                </NuxtLink>
            </div>
            <div class="miniCard03 miniCard  left-[33.75%] right-[33.75%] top-[37.96%] bottom-[0%]">
                <NuxtLink>
                    <button @click="loge"
                        class="bg_card w-full flex flex-row items-center bg-white rounded-[12px] transition ease-in-out delay-[30ms]">
                        <img class=" rounded-tl-[12px] rounded-bl-[12px] w-[121px] left-0 top-0 bottom-0"
                            src="/Rectanglens.png" alt="">
                        <h1
                            class="logements daFont ml-[24px] w-[88px] h-[19px] left-[145px] font-[600] text-[16px] leading-[19px]">
                            Expériences
                        </h1>
                    </button>
                </NuxtLink>
            </div>
            
        </div>

    </div>
</template>

<script>
export default {
    methods: {
        aventurez: () => {
            document.querySelector('#aventurez').scrollIntoView({
                behavior: 'smooth'
            })
        },
        loge: () => {
            document.querySelector('#loge').scrollIntoView({
                behavior: 'smooth'
            })
        },
        exp: () => {
            document.querySelector('#exp').scrollIntoView({
                behavior: 'smooth'
            })
        },

    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.daFont {
    font-family: 'Roboto', sans-serif;
}

.miniCard {
    filter: drop-shadow(0px 0px 15px rgba(0, 0, 0, 0.15));
}

.bg_card {
    color: #484848;
}

.bg_card:hover {
    background: #FF5A5F;
    color: white;
}
</style>
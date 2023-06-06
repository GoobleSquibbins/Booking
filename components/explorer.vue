<template>
    <div class="daFont flex flex-col md:items-start items-center md:w-[1208px] w-full mt-[30px]">
        <h1
            class="md:w-[181px] w-full md:ml-0 ml-[10px] h-[28px] not-italic font-[700] text-[24px] leading-[28px] text-[#484848] md:mb-[24px] mb-[10px]">
            Explorer Airbnb
        </h1>
        <div class="grid grid-cols-3 gap-[16px] justify-center md:w-full w-[97%]">
            <div class="miniCard01 miniCard w-full">
                <NuxtLink>
                    <button @click="aventurez"
                        class="bg_card w-full flex flex-row items-center bg-white md:rounded-[12px] rounded-[4px] transition ease-in-out delay-[30ms]">
                        <img class=" md:rounded-tl-[12px] rounded-tl-[4px] md:rounded-bl-[12px] rounded-bl-[4px] md:w-[121px] w-[70px] left-0 top-0 bottom-0"
                            src="/Rectangle4.png" alt="">
                        <h1
                            class="logements  daFont md:ml-[24px] ml-[8px] font-[600] md:text-[16px] text-[12px] md:leading-[19px] leading-[14px]">
                            Aventures
                        </h1>
                    </button>
                </NuxtLink>
            </div>
            <div class="miniCard02 miniCard w-full">
                <NuxtLink>
                    <button @click="loge"
                        class="bg_card w-full flex flex-row items-center bg-white md:rounded-[12px] rounded-[4px] transition ease-in-out delay-[30ms]">
                        <img class=" md:rounded-tl-[12px] rounded-tl-[4px] md:rounded-bl-[12px] rounded-bl-[4px] md:w-[121px] w-[70px] left-0 top-0 bottom-0"
                            src="/Rectanglehrzn.png" alt="">
                        <h1
                            class="logements  daFont md:ml-[24px] ml-[5px] font-[600] md:text-[16px] text-[12px] md:leading-[19px] leading-[14px]">
                            Logements
                        </h1>
                    </button>
                </NuxtLink>
            </div>
            <div class="miniCard02 miniCard w-full">
                <NuxtLink>
                    <button @click="exp"
                        class="bg_card w-full flex flex-row items-center bg-white md:rounded-[12px] rounded-[4px] transition ease-in-out delay-[30ms]">
                        <img class=" md:rounded-tl-[12px] rounded-tl-[4px] md:rounded-bl-[12px] rounded-bl-[4px] md:w-[121px] w-[70px] left-0 top-0 bottom-0"
                            src="/Rectanglens.png" alt="">
                        <h1
                            class="logements  daFont md:ml-[24px] ml-[5px] font-[600] md:text-[16px] text-[12px] md:leading-[19px] leading-[14px]">
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
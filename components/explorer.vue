<template>
    <div class="daFont absolute h-[137px] left-[80px] right-[80px] top-[838px]">
        <h1
            class="absolute w-[181px] h-[28px] top-0 left-0 not-italic font-[700] text-[24px] leading-[28px] text-[#484848]">
            Explorer Airbnb
        </h1>
        <div
            class="miniCard01 miniCard absolute left-[0%] right-[67.58%] top-[37.96%] bottom-[0%]">
            <NuxtLink to="#">
                <button class="bg_card absolute left-0 top-0 right-0 bottom-0 bg-white rounded-[12px] transition ease-in-out delay-[30ms]">
                    <h3
                        class="logements topcalctxt absolute w-[88px] h-[19px] left-[145px] font-[600] text-[16px] leading-[19px]">
                        Logements
                    </h3>
                    <img class="absolute rounded-tl-[12px] rounded-bl-[12px] w-[121px] left-0 top-0 bottom-0"
                        src="/Rectangle4.png" alt="">
                </button>
            </NuxtLink>

        </div>
        <div
            class="miniCard02 miniCard absolute left-[33.75%] right-[33.75%] top-[37.96%] bottom-[0%]">
            <NuxtLink>
                <button class="bg_card absolute left-0 top-0 right-0 bottom-0 bg-white rounded-[12px] transition ease-in-out delay-[30ms]">
                    <h3
                        class="experiences topcalctxt absolute w-[81px] h-[19px] left-[145px] font-[600] text-[16px] leading-[19px]">
                        Expériences
                    </h3>
                    <img class="absolute rounded-tl-[12px] rounded-bl-[12px] w-[121px] left-0 top-0 bottom-0"
                        src="/Rectanglehrzn.png" alt="">
                </button>
            </NuxtLink>
        </div>
        <div
            class="miniCard03 miniCard absolute left-[67.58%] right-[0%] top-[37.96%] bottom-[0%]">
            <button class="bg_card absolute left-0 top-0 right-0 bottom-0 bg-white rounded-[12px] transition ease-in-out delay-[30ms]">
                <h3
                    class="aventures topcalctxt absolute w-[81px] h-[19px] left-[145px] font-[600] text-[16px] leading-[19px]">
                    Aventures
                </h3>
                <img class="absolute rounded-tl-[12px] rounded-bl-[12px] w-[121px] left-0 top-0 bottom-0"
                    src="/Rectanglens.png" alt="">
            </button>
        </div>
    </div>
</template>

<script setup>

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

.daFont {
    font-family: 'Roboto', sans-serif;
}

.miniCard {
    filter: drop-shadow(0px 0px 15px rgba(0, 0, 0, 0.15));
}

.bg_card{
    color: #484848;
}

.bg_card:hover {
    background: #FF5A5F;
    color: white;
}

.topcalctxt {
    top: calc(50% - 19px/2);
}</style>
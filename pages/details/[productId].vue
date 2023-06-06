<template>
    <div class="daFont w-full flex flex-col items-center">
        <div class="md:w-[1208px] w-full md:pl-0 pl-[10px] md:pr-0 pr-[10px]">
            <DetHero />
            <div class="grid grid-cols-3 gap-[16px] w-full mt-[24px] pb-[50px]">
                <div class="col-span-2">
                    <DetInfo/>
                </div>
                <DetCheckout/>
            </div>  
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
</style>
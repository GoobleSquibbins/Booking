<template>
    <div class="flex flex-col items-center pb-[100px]">
        <div class="w-full md:w-[1366px] flex flex-col items-center relative">
            <!-- <div class="h-[750px] w-[1366px] relative">
                <Hero />
                <Header />
            </div> -->

            <Explorer />
            <!-- <Hebergement /> -->
            <Aventurez />
            <MondeEntier />
            <BienNotees />
            <ALaUne />
        </div>
    </div>
</template>

<script setup>

</script>

<style>
body::-webkit-scrollbar {
    width: 5px;
}

body::-webkit-scrollbar-track {
    background: transparent;
}

body::-webkit-scrollbar-thumb {
    background: #FF5A5F;
    border-radius: 4px;
}

body {
    overflow: overlay;
}
</style>
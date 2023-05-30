<template>
    <div class="flex flex-col items-center">
        <div class="w-full h-full absolute md:w-[1366px] md:h-[4096px] md:relative">
            <Hero />
            <Header />
            <Explorer />
            <Hebergement />
            <Aventurez />
            <MondeEntier />
            <BienNotees/>
            <ALaUne/>
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
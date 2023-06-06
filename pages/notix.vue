<template>
    <div class="flex flex-col items-center">
        <div class="w-[500px] relative h-[300px] border-[1px] border-black bg-white mt-[100px] flex flex-col items-center">
            <NuxtLink to="/seeAll">
            <button class="absolute right-[10px] top-[10px]">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                    stroke="currentColor" class="w-6 h-6">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                </svg>
            </button>
            </NuxtLink>
            <h1 class="font-[500] text-[24px] leading-[28px] text-black text-center w-full mt-[10px]">
                Item added to cart
            </h1>
            <img class="w-[300px] mb-[10px]"
                src="https://previews.123rf.com/images/ostill/ostill1112/ostill111200171/11752883-man-portrait-ok-sign-cheerful-studio-isolated-on-white-background.jpg"
                alt="">
        </div>
    </div>
</template>



<style lang="scss" scoped></style>
<template>
    <div v-for="item in stuff.products.filter(
        function (i) { return i.id == productId })"
        class="w-full border-[1px] border-black rounded-[10px] flex flex-col items-start">
        <div class="inside m-[30px]">
            <div class="head grid grid-cols-2 gap-10">
                <h1 class="text-[24px] leading-[28px] font-[300] text-[#484848]">
                    ${{ item.price }}
                </h1>
                <div class="rating flex flex-row items-center ml-[100px]">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"
                        class="w-3 h-3 mr-[5px]">
                        <path fill-rule="evenodd"
                            d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z"
                            clip-rule="evenodd" />
                    </svg>
                    <p>
                        {{ item.rating }}
                    </p>
                </div>
            </div>
            <div class="form w-full flex flex-col items-center mt-[15px]">
                <form>
                    <div class="dates w-full grid grid-cols-2 gap-0">
                        <div class="in">
                            <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                                Check-in
                            </label>
                            <input
                                class="focus:outline-none box-border p-[10px] text-center rounded-tl-[4px] rounded-bl-[4px] border-[1px] border-[#767676] w-[166px] h-[60px] left-0"
                                type="date" placeholder="DD/MM/YYYY">
                        </div>
                        <div class="in">
                            <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                                Check-out
                            </label>
                            <input
                                class="focus:outline-none box-border p-[10px] rounded-tr-[4px] rounded-br-[4px] border-[1px] border-[#767676] w-[166px] h-[60px] left-0"
                                type="date" >
                        </div>
                    </div>
                    <div class="guests mt-[5px]">
                        <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                            Number of Guests
                        </label>
                        <br>
                        <input type="number" class="focus:outline-none
                        text-[30px] pl-[30px] w-full h-[60px] border-[1px] border-[#767676] rounded-[4px]">
                    </div>
                    <div class="submit mt-[20px] float-right">
                        <button class="bg-[#FF5A5F] text-white p-[10px] rounded-[4px] border-[1px] border-[#FF5A5F]
                        hover:bg-white hover:border-[1px] hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                        transition ease-in-out delay-[30ms]">
                            RESERVE
                        </button>
                    </div>
                </form>
            </div>
        </div>

    </div>
</template>

<script setup>
const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products')
</script>

<style lang="scss" scoped></style>
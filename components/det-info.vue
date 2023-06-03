<template>
    <div v-for="item in stuff.products.filter(
        function (i) { return i.id == productId })" class="w-full">
        <div class="head flex flex-row items-center w-full">
            <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
               Product by : {{ item.brand }}
            </h1>
            <div class="img w-[50px] h-[50px] ml-auto">
                <img class="float-right w-[50px] h-[50px] rounded-[50%] outline outline-[1px] outline-black outline-offset-[3px]" :src="item.thumbnail" alt="">
            </div>
        </div>
        <div class="facility grid grid-cols-3 gap-[16px] w-full mt-[20px] border-b-[1px] pb-[20px] border-[#767676]">
            <div class="card01 w-full bg-white border-[1px] border-[#767676] rounded-[4px] h-[60px] shadow-lg
                            flex flex-row items-center p-[10px] text-[16px] leading-[19px] font-[300] text-[#484848]">
                <p>
                    Ratings : {{ item.rating }}
                </p>
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="#484848" class="w-3 h-3 justify-center items-center ml-[5px]">
                    <path fill-rule="evenodd"
                        d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401z"
                        clip-rule="evenodd" />
                </svg>
            </div>
            <div class="card02 w-full bg-white border-[1px] border-[#767676] rounded-[4px] h-[60px] shadow-lg
                        flex flex-row items-center p-[10px] text-[16px] leading-[19px] font-[300] text-[#484848]">
                <p>
                    Category : {{ item.category }}
                </p>
            </div>
            <div class="card03 w-full bg-white border-[1px] border-[#767676] rounded-[4px] h-[60px] shadow-lg
                    flex flex-row items-center p-[10px] text-[16px] leading-[19px] font-[300] text-[#484848]">
                <p>
                    Stock : {{ item.stock }}
                </p>
            </div>
        </div>
        <div class="service w-full flex flex-col items-start mt-[20px] border-b-[1px] border-[#767676] pb-[20px]">
            <p class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                {{ item.description }}
            </p>
        </div>

        <div class="host mt-[20px]">

            <div class="hostCardHolder flex flex-col items-center bg-[#ededed] w-full rounded-[12px] mt-[24px]">
                <div
                    class="hostCard grid grid-cols-3 gap-[5px] bg-white rounded-[20px] w-[60%] mt-[30px] mb-[30px] shadow-xl">
                    <div class="w-full hostProfile flex flex-col items-center col-span-2 p-[75px]">
                        <img class="h-[100px] w-[100px] rounded-[50%] outline outline-[1px] outline-black outline-offset-[5px]" :src="item.thumbnail" alt="">
                        <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848] mt-[15px]">
                            {{ item.title }}
                        </h1>
                        <p class="font-[300] text-[14px] leading-[18px] text-[#767676] mt-[10px]">
                            {{ item.category }}
                        </p>
                    </div>
                    <div class="w-full hostRating flex flex-col items-center p-[25px] justify-center">
                        <div class="stock w-full flex flex-col items-start border-b-[1px] border-[#767676] pb-[10px]">
                            <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                                {{ item.stock }}
                            </h1>
                            <p class="font-[300] text-[14px] leading-[21px] text-[#484848] ">
                                Stock
                            </p>
                        </div>
                        <div
                            class="rating mt-[10px] w-full flex flex-col items-start border-b-[1px] border-[#767676] pb-[10px]">
                            <div class="rateNum flex flex-row items-center">
                                <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                                    {{ item.rating }}
                                </h1>
                                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="#484848"
                                    class="w-3 h-3 ml-[5px]">
                                    <path fill-rule="evenodd"
                                        d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z"
                                        clip-rule="evenodd" />
                                </svg>
                            </div>
                            <p class="font-[300] text-[14px] leading-[21px] text-[#484848] ">
                                Rating
                            </p>
                        </div>
                        <div class="price mt-[10px] w-full flex flex-col items-start">
                            <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                                $ {{ item.price }}
                            </h1>
                            <p class="font-[300] text-[14px] leading-[21px] text-[#484848] ">
                                Price
                            </p>
                        </div>
                    </div>
                </div>

                <!-- <div class="shortInfo w-[60%] flex flex-col items-start">
                    <p class="font-[300] text-[18px] leading-[21px] text-[#484848] m-[10px]">
                        Where I went to school : ___
                    </p>
                    <p class="font-[300] text-[18px] leading-[21px] text-[#484848] m-[10px]">
                        Speaks ___ and ___
                    </p>
                    <p class="font-[300] text-[18px] leading-[21px] text-[#484848] m-[10px]">
                        Lives in ___
                    </p>
                    <p class="font-[300] text-[18px] leading-[21px] text-[#484848] m-[10px]">
                        Pets : ___
                    </p>
                </div>

                <div class="hostDesc w-[60%] text-start">
                    <p class="font-[300] text-[16px] leading-[19px] text-[#484848] mt-[20px]">
                        {{ item.description }}
                    </p>
                </div>
                <div class="mr-[363px]">
                    <NuxtLink to="#">
                        <div
                            class="flex flex-row items-center text-[#484848] hover:text-black stroke-[#484848] hover:stroke-black mt-[10px]">
                            <h1 class="font-[700] text-[18px] leading-[21px] mr-[10px] underline">
                                Show more
                            </h1>
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="3"
                                class="w-4 h-5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
                            </svg>
                        </div>
                    </NuxtLink>
                </div>
                <div class="msgHost w-[60%] border-b-[1px] border-[#767676] pb-[20px]">
                    <button
                        class="bg-[#FF5A5F] text-white font-[700] text-[19px] leading-[21px] p-[15px] rounded-[7px] mt-[20px]">
                        Message Host
                    </button>
                </div> -->
                <div class="toprotect w-[60%] text-start mt-[20px] pb-[30px]">
                    <p class="text-[12px] leading-[15px] font-[300] text-[#484848]">
                        To protect your payment, never transfer money or communicate outside of the Airbnb website or app.
                    </p>
                </div>
            </div>

            <!-- <div class="placeInfo text-start mt-[30px]">
                <div class="pb-[20px] border-b-[1px] border-[#767676] ">
                    <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                        About this place
                    </h1>
                    <p class="mt-[8px] font-[300] text-[14px] leading-[17px] text-[#484848]">
                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. In nemo ratione porro. Expedita, beatae
                        similique! Quaerat corrupti distinctio sequi obcaecati repellat culpa, ab dolore accusamus aperiam.
                        Tempore hic eligendi temporibus incidunt eaque? Repellendus minus eos aliquam, iste in, provident
                        cupiditate numquam itaque officia soluta harum quaerat illo eum id, explicabo placeat vero deleniti
                        impedit ipsum autem voluptas quis! Fuga inventore iusto cum. Expedita omnis modi, vero voluptate
                        velit officia nisi dolorum sequi accusantium quod. Sint illo ducimus harum minus molestiae numquam
                        ea a rerum reprehenderit ipsa nesciunt, incidunt, dolorem commodi. Harum recusandae sint provident!
                        Ducimus incidunt, blanditiis corporis cumque magni consequuntur quos illum ipsum? Praesentium esse
                        tenetur sapiente quo. Delectus neque exercitationem sit vel facilis rerum, beatae, tenetur
                        perferendis amet impedit voluptatem, doloremque odio repudiandae quas assumenda aliquam magnam
                        similique error minus dolore non? In commodi necessitatibus, delectus placeat porro quidem, animi
                        doloribus facilis saepe temporibus numquam aliquam, cupiditate eligendi.
                    </p>
                </div>

                <div class="amenities flex flex-col items-start w-full mt-[20px]">
                    <h1 class="font-[700] text-[24px] leading-[28px] text-[#484848]">
                        What this place offers
                    </h1>
                    <div class="ameItemHolder grid grid-cols-2 gap-[16px] w-full mt-[15px]">
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                        <div class="ameItems w-full flex flex-col items-start m-[10px]">
                            <h1 class="font-[300] text-[16px] leading-[19px] text-[#484848]">
                                amenity
                            </h1>
                        </div>
                    </div>
                </div>
            </div> -->
        </div>
    </div>
</template>

<script setup>
const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products?limit=0')
</script>

<style lang="scss" scoped></style>
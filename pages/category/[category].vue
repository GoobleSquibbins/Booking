<template>
    <div class="w-full flex flex-col items-center ">
        <div class="h-[900px]">
            <div class="grid grid-cols-4 gap-[16px] justify-start w-[1340px] mt-[15px] pb-[80px]">
                <div v-for=" item in filteredItems.products" class="w-full flex flex-col items-start relative">
                    <Swiper class="groupSwiper w-[323px] h-[200px]"
                        :modules="[SwiperAutoplay, SwiperEffectCreative, SwiperPagination, SwiperNavigation]"
                        :slides-per-view="1" :loop="false" :effect="'creative'" :navigation="true" :hashNavigation="{
                            watchState: true,
                        }" :pagination="{ clickable: true }" :creative-effect="{
    prev: {
        shadow: false,
        translate: ['-100%', 0, -1],
    },
    next: {
        translate: ['100%', 0, 0],
    },
}">
                        <SwiperSlide v-for="image in item.images" class="w-[323px] h-[200px]">
                            <NuxtLink :to="'/details/' + item.id" class="w-[323px] h-[200px]">
                                <img :src="image" alt=""
                                    class="w-[323px] h-[200px] object-cover duration-1000 rounded-[4px]">
                            </NuxtLink>
                        </SwiperSlide>
                    </Swiper>

                    <!-- <NuxtLink :to="'/details/' + item.id" class="w-full h-full">
                        <img class="w-full h-[200px] rounded-[4px] object-cover mb-[8px]" :src="item.thumbnail" alt="">
                    </NuxtLink> -->

                    <!-- <button id="left" @click="left"
                        class="hover:bg-white hover:stroke-[#FF5A5F] transition ease-in-out delay-[30ms] stroke-white w-[30px] h-[30px] border-[1px] border-[#FF5A5F] absolute top-[85px] left-[7px] rounded-[50%] bg-[#FF5A5F]">
                        <div class="w-full h-full flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                class="w-3 h-3">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
                            </svg>
                        </div>
                    </button>
                    <button id="right" @click="right"
                        class="hover:bg-white hover:stroke-[#FF5A5F] stroke-white transition ease-in-out delay-[30ms] z-[100] w-[30px] h-[30px] border-[1px] border-[#FF5A5F] absolute top-[85px] right-[7px] rounded-[50%] bg-[#FF5A5F]">
                        <div class="w-full h-full flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                class="w-3 h-3">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
                            </svg>

                        </div>
                    </button> -->

                    <div class="row1 grid grid-cols-5 w-full mt-[8px]">
                        <NuxtLink :to="'/category/' + item.category" class="w-full h-full col-span-2 ">
                            <button class="border-[1px] text-black border-black rounded-[2px] box-border w-full h-[30px] hover:border-[#FF5A5F] hover:text-[#FF5A5F] transition ease-in-out delay-[30ms]">
                                <div class="text-[10px] leading-[12px] font-[700] uppercase w-full h-[30px]">
                                    <div class="w-full h-full flex flex-row items-center justify-center">
                                        {{ item.category }}
                                    </div>
                                </div>
                            </button>
                        </NuxtLink>

                        <div class="flex flex-row items-center justify-center w-full h-full ml-[13px] col-span-2">
                            <p class="font-[400] text-[12px] leading-[14px] text-[#767676] w-full">
                                {{ item.title }}
                            </p>
                        </div>
                        <div class="justify-end flex flex-row items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="#484848" class="w-3 h-3">
                                <path fill-rule="evenodd"
                                    d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401z"
                                    clip-rule="evenodd" />
                            </svg>
                            <p class="font-[500] text-[12px] leading-[14px] text-[#484848] ml-[4px]">
                                {{ item.rating }}
                            </p>
                        </div>
                    </div>

                    <div class="row2 flex flex-col items-start w-full">
                        <p class="w-full font-[400] text-[14px] leading-[21px] text-[#484848] mt-[8px]">
                            ${{ item.price }}
                        </p>

                        <div class="w-full mt-[8px]">
                            <button class="w-full" @click="addToCart(item.id, qty)">
                                <div
                                    class="                                                                                                                                               w-full h-[28px]
                                                                                                                                                                                                                flex flex-row items-center justify-center
                                                                                                                                                                                                                hover:text-[#FF5A5F] hover:stroke-[#FF5A5F] hover:bg-white
                                                                                                                                                                                                                text-white stroke-white bg-[#FF5A5F] border-[1px] border-[#FF5A5F] rounded-[4px]
                                                                                                                                                                                                                transition ease-in-out delay-[30ms]">
                                    <p class="text-[14px] leading-[18px] font-[300]">
                                        Add to cart
                                    </p>
                                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                        stroke-width="1.5" class="w-5 h-5">
                                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                                    </svg>
                                </div>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
// let { data: catIt } = await useFetch('https://dummyjson.com/products/categories')
</script>

<script>
export default {
    data() {
        return {
            search: '',
            filteredItems: [],
            catIt: [],
            pickedCat: '',
            turnOn: false,
            showCart: false,
            cart: '',
            qty: 1
        }
    }
    ,
    methods: {
        async addToCart(id, qty) {
            let currCategory = useRoute().params
            console.log(id)
            if (this.showCart == true) {
                document.getElementById('Emptycart').style.display = "block";
                document.getElementById('goToCheckout').style.display = "block";
            }

            let { data: product } = await useFetch('https://dummyjson.com/products/' + id);
            let dataProduct = product._rawValue;
            dataProduct.qty = qty;
            console.log(dataProduct)

            if (!localStorage.getItem("a")) {
                let array = []
                dataProduct.cartId = 1
                array.push(dataProduct)
                localStorage.setItem("a", JSON.stringify(array))
                console.log(JSON.parse(localStorage.getItem("a")))
                console.log(dataProduct)
                this.cart = JSON.parse(localStorage.getItem("a"))

            } else {
                let stuffAlreadyInside = JSON.parse(localStorage.getItem("a"))
                console.log(stuffAlreadyInside + ' cheese')
                let newArray = []
                for (let i = 0; i < stuffAlreadyInside.length; i++) {
                    if (!newArray.includes(stuffAlreadyInside[i].id)) {
                        newArray.push(stuffAlreadyInside[i].id)
                    }
                }
                console.log(newArray + ' poof')
                if (!newArray.includes(dataProduct.id)) {
                    dataProduct.cartId = stuffAlreadyInside.length + 1
                    stuffAlreadyInside.push(dataProduct)
                    localStorage.setItem("a", JSON.stringify(stuffAlreadyInside));
                    this.cart = JSON.parse(localStorage.getItem("a"))
                } else {
                    for (let j = 0; j < stuffAlreadyInside.length; j++) {
                        console.log('shidded')
                        if (stuffAlreadyInside[j].id === id) {
                            if (stuffAlreadyInside[j].qty < stuffAlreadyInside[j].stock) {
                                stuffAlreadyInside[j].qty += 1
                            } else {
                                console.log('we run out of stock mate sorry')
                            }
                            localStorage.setItem("a", JSON.stringify(stuffAlreadyInside))
                            this.cart = JSON.parse(localStorage.getItem("a"))
                        }
                    }
                    console.log('shid and camed')
                }
                console.log(dataProduct)

            }
            console.log(currCategory)

        }
        ,
        selCat() {
            let param = useRoute().params
            this.pickedCat = param.category
            console.log(this.pickedCat)
        }
        ,


        async filterDaData() {
            console.log(this.pickedCat)
            if (localStorage.getItem("a")) {
                this.cart = JSON.parse(localStorage.getItem("a"))
            }
            let { data: data } = await useFetch('https://dummyjson.com/products/categories');
            this.catIt = data
            if (this.search === '') {
                if (this.pickedCat === '') {
                    let { data: data } = await useFetch('https://dummyjson.com/products?limit=0');
                    this.filteredItems = data
                } else {
                    let { data: data } = await useFetch('https://dummyjson.com/products/category/' + this.pickedCat);
                    this.filteredItems = data
                }

                console.log(this.pickedCat + ' cheese')
            } else {
                let { data: data } = await useFetch('https://dummyjson.com/products/search?q=' + this.search.toLowerCase());
                this.filteredItems = data
                console.log('cheeseeeee ')
            }
        }

    }
    ,
    beforeMount() {
        this.filterDaData()
        this.selCat()
        // this.loadCart()
    }
}
</script>

<style scoped>
.catHolder::-webkit-scrollbar {
    height: 5px;
}

.catHolder::-webkit-scrollbar-track {
    background: transparent;
}

.catHolder::-webkit-scrollbar-thumb {
    background: #FF5A5F;
    border-radius: 4px;
}

.cart::-webkit-scrollbar {
    width: 5px;
}

.cart::-webkit-scrollbar-track {
    background: transparent;
}

.cart::-webkit-scrollbar-thumb {
    background: #FF5A5F;
    border-radius: 4px;
}
</style>
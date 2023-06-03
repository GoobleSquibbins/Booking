<template>
    <div class="h-[900px]">
        <div class="w-[1208px] flex flex-row items-center">
            <div class="border-[1px] border-black rounded-[20px] w-[300px] p-[10px] flex flex-row items-center">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5">
                    <path fill-rule="evenodd"
                        d="M9 3.5a5.5 5.5 0 100 11 5.5 5.5 0 000-11zM2 9a7 7 0 1112.452 4.391l3.328 3.329a.75.75 0 11-1.06 1.06l-3.329-3.328A7 7 0 012 9z"
                        clip-rule="evenodd" />
                </svg>
                <input type="text" placeholder="Search items" class="focus:outline-none w-full ml-[10px]" v-model="search"
                    @keyup="filterDaData()">
            </div>
            <div
                class="ml-auto border-[1px] border-black rounded-[30px] w-[100px] flex flex-col items-end justify-center relative">
                <button @click="showC" class="flex flex-row items-center justify-center w-full p-[5px] ">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                        stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round"
                            d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z" />
                    </svg>
                    <p class="font-[500] text-[14px] leading-[18px] ml-[10px]">
                        Cart
                    </p>
                </button>

                <div id="cart" class="cart hidden pt-[5px]
                                            w-[300px] h-[700px] border-[1px] border-black shadow-2xl bg-white absolute top-[50px] rounded-[4px]
                                            overflow-y-scroll  flex-col items-center">
                    <div v-for="item in cart"
                        class="w-[280px] grid grid-cols-5 gap-[5px] justify-start border-b-[1px] border-black m-[5px]">
                        <NuxtLink :to="'/details/' + item.id">
                            <img :src="item.thumbnail" class="h-[50px] w-[50px] object-cover" alt="">
                        </NuxtLink>
                        <div class="w-full h-full flex items-center justify-start col-span-2">
                            <NuxtLink :to="'/details/' + item.id">
                                <p>
                                    {{ item.cartId }}
                                </p>
                            </NuxtLink>

                        </div>

                        <div class="w-full h-full flex items-center justify-start">
                            <p>
                                {{ item.qty }} unit
                            </p>
                        </div>

                        <div class="w-full h-full flex flex-row items-center justify-center">
                            <button @click="removeItemFromCart(item.cartId)"
                                class="bg-[#FF5A5F] text-white border-[#FF5A5F] w-full h-[20px] rounded-[5px] text-[12px] leading-[14px]">
                                remove
                            </button>
                        </div>
                    </div>
                </div>
                <div id="Emptycart" class="deleteAll w-[100px] absolute right-[200px] hidden">
                    <button @click="emptyTheCart()"
                        class="w-full h-full border-[1px] border-[#FF5A5F] p-[5px] rounded-[20px] text-white bg-[#FF5A5F]">
                        Empty cart
                    </button>
                </div>
            </div>
        </div>

        <div
            class="catHolder flex flex-row items-center w-[1208px] gap-[10px] h-[50px] overflow-x-scroll mt-[20px] pb-[10px]">
            <div class="w-full h-full">
                <button @mouseup="selCat('')" @click="filterDaData()" autoFocus class="
                                hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                                focus:border-[#FF5A5F] focus:text-white focus:bg-[#FF5A5F] focus:outline-none
                                w-[150px] flex flex-row justify-center items-center h-full text-black border-[1px] border-black rounded-[20px]
                                transition ease-in-out delay-[30ms]">

                    <p class="font-[500] text-[12px] leading-[14px]  uppercase">
                        All item
                    </p>
                </button>
            </div>

            <div v-for="cat in catIt" class="w-full h-full">
                <button @mouseup="selCat(cat)" @click="filterDaData()"
                    class="
                                                                                                                                                    hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                                                                                                                                                    focus:border-[#FF5A5F] focus:text-white focus:bg-[#FF5A5F] 
                                                                                                                                                    w-[150px] flex flex-row justify-center items-center h-full text-black border-[1px] border-black rounded-[20px]
                                                                                                                                                    transition ease-in-out delay-[30ms]">

                    <p class="font-[500] text-[12px] leading-[14px]  uppercase">
                        {{ cat }}
                    </p>
                </button>
            </div>
        </div>
        <!-- <button v-if="turnOn" @click="skibidibobmdada"
            class="bg-[#FF5A5F] border-[1px] border-[#FF5A5F] bg-[#FF5AF] text-white w-[70px] rounded-[20px] mt-[10px]">
            <h1 class="font-[500] text-[16px] leading-[19px] p-[10px]">
                Back
            </h1>
        </button> -->

        <div class="grid grid-cols-4 gap-[16px] justify-start w-[1208px] mt-[15px] pb-[80px]">
            <div v-for=" item in filteredItems.products" class="w-full flex flex-col items-start">
                <NuxtLink :to="'/details/' + item.id" class="w-full h-full">
                    <img class="w-full h-[200px]
                                                                                                rounded-[4px] object-cover mb-[8px]"
                        :src="item.thumbnail" alt="">
                </NuxtLink>

                <div class="row1 grid grid-cols-5 w-full">
                    <div
                        class="col-span-2 border-[1px] border-black rounded-[2px] box-border w-full h-[30px]
                                                                                                                                                                                                                    hover:border-[1px] hover:border-[#FF5A5F] hover:text-[#FF5A5F] text-black transition ease-in-out delay-[30ms]">
                        <button class="text-[10px] leading-[12px] font-[700] uppercase w-full h-[30px]">
                            <div class="w-full h-full flex flex-row items-center justify-center">
                                {{ item.category }}
                            </div>
                        </button>
                    </div>
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
                        <button class="w-full" @click="addToCart(item.id, this.qty)">
                            <div
                                class="
                                                                                                                                                                                            w-full h-[28px]
                                                                                                                                                                                            flex flex-row items-center justify-center
                                                                                                                                                                                            hover:text-[#FF5A5F] hover:stroke-[#FF5A5F] hover:bg-white
                                                                                                                                                                                            text-white stroke-white bg-[#FF5A5F] border-[1px] border-[#FF5A5F] rounded-[4px]
                                                                                                                                                                                            transition ease-in-out delay-[30ms]">
                                <p class="text-[14px] leading-[18px] font-[300]">
                                    Add to cart
                                </p>
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                                    class="w-5 h-5">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                                </svg>
                            </div>
                        </button>
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
        // loadCart() {
        //     // localStorage.clear()
        //     this.cart = JSON.parse(localStorage.getItem("a"))
        //     console.log('real')
        // }
        // ,
        emptyTheCart() {
            localStorage.clear()
            this.cart = JSON.parse(localStorage.getItem("a"))
            document.getElementById('Emptycart').style.display = "none";
        }
        ,
        removeItemFromCart(cartId) {
            let stuffAlreadyInTheCartRn = JSON.parse(localStorage.getItem("a"))
            if (stuffAlreadyInTheCartRn.length === 1){
                document.getElementById('Emptycart').style.display = "none";
            }
            console.log(stuffAlreadyInTheCartRn)
            for (let l = 0; l < stuffAlreadyInTheCartRn.length; l++) {
                if (stuffAlreadyInTheCartRn[l].cartId === cartId) {
                    let indexu = cartId - 1
                    stuffAlreadyInTheCartRn.splice(indexu, 1)
                    localStorage.setItem("a", JSON.stringify(stuffAlreadyInTheCartRn))
                    this.cart = JSON.parse(localStorage.getItem("a"))
                    console.log(JSON.parse(localStorage.getItem("a")))
                    
                }
            }
        }
        ,
        async addToCart(id, qty) {
            if(this.showCart == true){
                document.getElementById('Emptycart').style.display = "block";
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
                    console.log(stuffAlreadyInside[10].id + ' camed');
                } else {
                    for (let j = 0; j < stuffAlreadyInside.length; j++) {
                        console.log('shidded')
                        if (stuffAlreadyInside[j].id === id) {
                            stuffAlreadyInside[j].qty += 1
                            localStorage.setItem("a", JSON.stringify(stuffAlreadyInside))
                            this.cart = JSON.parse(localStorage.getItem("a"))
                        }
                    }
                    console.log('shid and camed')
                }
                console.log(dataProduct)

            }

        }
        ,
        showC() {
            this.showCart = !this.showCart
            console.log(this.showCart)
            document.getElementById('Emptycart').style.display = "none";
            if (this.showCart == true) {
                document.getElementById('cart').style.display = "flex";
                if (JSON.parse(localStorage.getItem("a")).length === 0 ) {
                    document.getElementById('Emptycart').style.display = "none";
                } else {
                    document.getElementById('Emptycart').style.display = "block";
                }

            } else {
                document.getElementById('cart').style.display = "none";
                document.getElementById('Emptycart').style.display = "none";

            }
        }
        ,
        selCat(cat) {
            this.pickedCat = cat
        }
        ,
        async filterDaData() {
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


            // if (this.search === '') {
            //     let { data: data } = await useFetch('https://dummyjson.com/products/category/' + this.pickedCat.toLowerCase());
            //     this.filteredItems = data
            // } else {
            //     let { data: data } = await useFetch('https://dummyjson.com/products/category/' + this.pickedCat + '/search?q=' + this.search.toLowerCase());
            //     this.filteredItems = data
            //     // console.log(this.pickedCat + ' ' + this.search)
            // }

            // if (this.pickedCat === undefined) {
            //     let { data: data } = await useFetch('https://dummyjson.com/products');
            //     this.filteredItems = data

            // } else {
            //     let { data: data } = await useFetch('https://dummyjson.com/products/category/' + this.pickedCat.toLowerCase());
            //     this.filteredItems = data

            //     this.turnOn = true
            // }

            // if (this.search === '') {
            //     let { data: data } = await useFetch('https://dummyjson.com/products');
            //     this.filteredItems = data
            // } else {
            //     let { data: data } = await useFetch('https://dummyjson.com/products/search?q=' + this.search.toLowerCase());
            //     this.filteredItems = data
            //     // console.log(this.pickedCat + ' ' + this.search)
            // }
            // console.log(this.pickedCat)
        }

    }
    ,
    beforeMount() {
        this.filterDaData()
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
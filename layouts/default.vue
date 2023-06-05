<template>
    <div class="w-full flex flex-col items-center mt-[10px]">
        <div class="w-[1340px] flex flex-row items-center mt-[10px] relative">
            <div class="border-[1px] border-black rounded-[20px] w-[300px] p-[10px] flex flex-row items-center">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5">
                    <path fill-rule="evenodd"
                        d="M9 3.5a5.5 5.5 0 100 11 5.5 5.5 0 000-11zM2 9a7 7 0 1112.452 4.391l3.328 3.329a.75.75 0 11-1.06 1.06l-3.329-3.328A7 7 0 012 9z"
                        clip-rule="evenodd" />
                </svg>
                <input type="text" placeholder="Search items" class="focus:outline-none w-full ml-[10px]" v-model="search"
                    v-on:keyup.enter="searchItems">
            </div>

            <NuxtLink to="/login">
                <button id="loginBtn"
                    class="absolute right-[115px] top-[5px] rounded-[20px] text-black hover:text-[#FF5A5F] hover:border-[#FF5A5F] transition ease-in-out delay-[30ms] w-[70px] h-[35px] p-[5px] border-[1px] border-black">
                    <h1 class="font-[500] text-[14px] leading-[18px] ">
                        LOGIN
                    </h1>
                </button>
            </NuxtLink>

            <div
                class="ml-auto w-[100px] flex flex-col items-end justify-center relative ">
                <button @click="showC" class="flex flex-row items-center justify-center w-full p-[5px] hover:border-[#FF5A5F] text-black hover:text-[#FF5A5F] border-[1px] border-black rounded-[30px] transition ease-in-out delay-[30ms]">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                        stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round"
                            d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z" />
                    </svg>
                    <p class="font-[500] text-[14px] leading-[18px] ml-[10px]">
                        Cart
                    </p>
                </button>

                <div id="goToCheckout"
                    class="hidden payEverything z-[1201] absolute top-[540px] w-[290px] right-[5px] h-[30px]">
                    <button @click="checkout" class="bg-[#FF5A5F] rounded-[4px] text-center p-[5px] w-full h-full border-[1px] border-[#FF5A5F] text-white hover:bg-white hover:border-[#FF5A5F] hover:text-[#FF5A5F] transition ease-in-out delay-[30ms]">
                        <div class="flex flex-row items-center justify-center w-full h-full">
                            Go to checkout
                        </div>
                    </button>


                </div>

                <div id="cart" class="cart hidden pt-[5px] z-[1200] w-[300px] h-[525px] border-[1px] border-black shadow-2xl bg-white absolute top-[50px] rounded-[4px]
                        overflow-y-scroll  flex-col items-center">
                    <div v-for="item in cart"
                        class="w-[280px] grid grid-cols-5 gap-[5px] justify-start border-b-[1px] border-black m-[5px]">
                        <NuxtLink :to="'/details/' + item.id">
                            <img :src="item.thumbnail" class="h-[50px] w-[50px] object-cover" alt="">
                        </NuxtLink>
                        <div class="w-full h-full flex items-center justify-start col-span-2">
                            <NuxtLink :to="'/details/' + item.id">
                                <p>
                                    {{ item.title }}
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
                                class="hover:border-[#FF5A5F] hover:text-[#FF5A5F] hover:bg-white transition ease-in-out delay-[30ms] border-[1px] bg-[#FF5A5F] text-white border-[#FF5A5F] w-full h-[20px] rounded-[20px] text-[10px] leading-[14px]">
                                remove
                            </button>
                        </div>
                    </div>
                </div>
                <div id="Emptycart" class="deleteAll w-[100px] absolute right-[200px] hidden">
                    <button @click="emptyTheCart()"
                        class="w-full hover:border-[#FF5A5F] hover:text-[#FF5A5F] hover:bg-white transition ease-in-out delay-[30ms] h-full border-[1px] border-[#FF5A5F] p-[5px] rounded-[20px] text-white bg-[#FF5A5F]">
                        Empty cart
                    </button>
                </div>
            </div>
        </div>

        <div
            class="catHolder flex flex-row items-center w-[1340px]  gap-[10px] h-[50px] overflow-x-scroll mt-[20px] pb-[10px]">
            <div class="w-full h-full">
                <NuxtLink to="/seeAll" class="w-full h-full">
                    <button class="hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                                                            focus:border-[#FF5A5F] focus:text-white focus:bg-[#FF5A5F] focus:outline-none
                                                            w-[150px] flex flex-row justify-center items-center h-full text-black border-[1px] border-black rounded-[20px]
                                                            transition ease-in-out delay-[30ms]">

                        <p class="font-[500] text-[12px] leading-[14px]  uppercase">
                            All item
                        </p>
                    </button>
                </NuxtLink>

            </div>

            <div v-for="cat in catIt" class="w-full h-full">
                <button @mouseup="selCat(cat)" @click="filterDaData()"
                    class="hover:border-[#FF5A5F] hover:text-[#FF5A5F] focus:border-[#FF5A5F] focus:text-white focus:bg-[#FF5A5F] w-[150px] flex flex-row justify-center items-center h-full text-black border-[1px] border-black rounded-[20px] first-letter:transition ease-in-out delay-[30ms]">
                    <p class="font-[500] text-[12px] leading-[14px]  uppercase">
                        {{ cat }}
                    </p>
                </button>

            </div>
        </div>
    </div>
    <div>
        <slot></slot>
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
        loginCheck() {
            if (!localStorage.getItem("login")) {
                document.getElementById('loginBtn').style.display = "block";
            } else {
                document.getElementById('loginBtn').style.display = "none";
            }
        }
        ,
        checkout() {
            window.location.href = "/checkout"
        }
        ,
        emptyTheCart() {
            localStorage.clear()
            this.cart = JSON.parse(localStorage.getItem("a"))
            document.getElementById('Emptycart').style.display = "none";
            document.getElementById('goToCheckout').style.display = "none";
        }
        ,
        removeItemFromCart(cartId) {
            let stuffAlreadyInTheCartRn = JSON.parse(localStorage.getItem("a"))
            if (stuffAlreadyInTheCartRn.length === 1) {
                document.getElementById('Emptycart').style.display = "none";
                document.getElementById('goToCheckout').style.display = "none";
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
                    console.log(stuffAlreadyInside[10].id + ' camed');
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

        }
        ,
        showC() {
            this.cart = JSON.parse(localStorage.getItem("a"))
            this.showCart = !this.showCart
            console.log(this.showCart)
            document.getElementById('Emptycart').style.display = "none";
            document.getElementById('goToCheckout').style.display = "none";
            if (this.showCart == true) {
                document.getElementById('cart').style.display = "flex";
                if (JSON.parse(localStorage.getItem("a")).length === 0) {
                    document.getElementById('Emptycart').style.display = "none";
                    document.getElementById('goToCheckout').style.display = "none";
                } else {
                    document.getElementById('Emptycart').style.display = "block";
                    document.getElementById('goToCheckout').style.display = "block";
                }

            } else {
                document.getElementById('cart').style.display = "none";
                document.getElementById('Emptycart').style.display = "none";
                document.getElementById('goToCheckout').style.display = "none";

            }
        }
        ,
        selCat(cat) {
            this.pickedCat = cat
        }
        ,
        searchItems() {
            window.location.href = "/search/" + this.search
            console.log(this.search)

        }
        ,
        async filterDaData() {
            if (localStorage.getItem("a")) {
                this.cart = JSON.parse(localStorage.getItem("a"))
            }
            let { data: data } = await useFetch('https://dummyjson.com/products/categories');
            this.catIt = data

            if (this.pickedCat === '') {
                let { data: data } = await useFetch('https://dummyjson.com/products?limit=0');
                this.filteredItems = data
            } else {
                let { data: data } = await useFetch('https://dummyjson.com/products/category/' + this.pickedCat);
                window.location.href = "/category/" + this.pickedCat
                this.filteredItems = data
            }

            console.log(this.pickedCat + ' cheese')
        }

    }
    ,
    beforeMount() {
        this.filterDaData()
        this.loginCheck()
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
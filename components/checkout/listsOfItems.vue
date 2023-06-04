<template>
    <div class="w-fullmt-[30px]">
        <button id="Emptycart" @click="emptyTheCart"
            class=" bg-[#FF5A5F] border-[1px] border-[#FF5AF] text-white p-[5px] mt-[20px] ml-[10px] rounded-[20px] w-[130px]">
            Empty Cart
        </button>
        <div v-for="item in cart">
            <div class="w-full grid grid-cols-4 p-[10px] bg-[#D6D6D6] m-[10px]">
                <div class="flex items-center justify-start col-span-2 w-full h-full">
                    <p class="font-[400] text-[16px] leading-[19px] mr-[10px]">
                        {{ item.cartId }}.
                    </p>
                    <img class="h-[100px] w-[100px] object-cover" :src="item.thumbnail" alt="">
                    <h1 class="font-[400] text-[16px] leading-[19px] ml-[10px]">
                        {{ item.title }}
                    </h1>
                </div>
                <div class="w-full flex items-center justify-start">
                    <h1 class="font-[400] text-[16px] leading-[19px]">
                        Quantity of item : {{ item.qty }}
                    </h1>
                </div>
                <div class="w-full h-full flex flex-col items-end justify-center">
                    <h1>
                        ${{ item.price }}
                    </h1>
                    <button @click="removeItemFromCart(item.cartId)"
                        class="mt-[5px] bg-[#FF5A5F] text-white border-[#FF5A5F] w-[100px] h-[20px] rounded-[5px] text-[12px] leading-[14px]">
                        <div class="w-full h-full flex items-center justify-center">
                            remove
                        </div>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            cart: ''
        }
    }
    ,
    methods: {
        initializeCart() {
            this.cart = JSON.parse(localStorage.getItem("a"))
        }
        ,
        emptyTheCart() {
            localStorage.clear()
            this.cart = JSON.parse(localStorage.getItem("a"))
            window.location.href = "/seeAll"
        }
        ,
        removeItemFromCart(cartId) {
            let stuffAlreadyInTheCartRn = JSON.parse(localStorage.getItem("a"))
            if (stuffAlreadyInTheCartRn.length === 1) {
                this.cart = JSON.parse(localStorage.getItem("a"))
                window.location.href = "/seeAll"
            }
            console.log(stuffAlreadyInTheCartRn)
            for (let l = 0; l < stuffAlreadyInTheCartRn.length; l++) {
                if (stuffAlreadyInTheCartRn[l].cartId === cartId) {
                    let indexu = cartId - 1
                    stuffAlreadyInTheCartRn.splice(indexu, 1)
                    localStorage.setItem("a", JSON.stringify(stuffAlreadyInTheCartRn))
                    this.cart = JSON.parse(localStorage.getItem("a"))
                    console.log(JSON.parse(localStorage.getItem("a")))
                    window.location.href = "/checkout"

                }
            }
        }

    }
    ,
    beforeMount() {
        this.initializeCart()
    }
}
</script>

<style lang="scss" scoped></style>
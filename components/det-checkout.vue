<template>
    <div class="h-full w-full">
        <div v-for="item in stuff.products.filter(
            function (i) { return i.id == productId })"
            class="sticky top-[100px] w-full border-[1px] border-[#767676] rounded-[10px] flex flex-col items-start">
            <div class="inside p-[30px] w-full">
                <div class="head flex flex-col items-start w-full">
                    <div class="rating flex flex-row items-center mt-[5px]">
                        <p class="text-[24px] font-[700] leading-[28px] text-[#484848]">
                            {{ item.title }}
                        </p>
                    </div>
                    <h1 class="text-[24px] leading-[28px] font-[300] text-[#484848]">
                        $<span id="price" class="text-[24px] leading-[28px] font-[300] text-[#484848]">{{ item.price
                        }}</span>
                    </h1>
                    <p class="mt-[5px]">
                        Stock : <span id="stock">{{ item.stock }}</span>
                    </p>
                </div>
                <div class="form w-full flex flex-col items-center">
                    <div class="guests mt-[5px] w-full">
                        <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                            Number of Items
                        </label>
                        <br>

                        <input v-model="itemNum" type="number" @keyup="count()" class="
                                                        w-full h-[60px] 
                                                        border-[1px] border-[#767676] rounded-[4px]
                                                        text-center text-[16px] leading-[19px]" />

                    </div>
                    <div class="submit mt-[20px] w-full">
                        <NuxtLink to="/notix" class="w-full h-full">
                            <button @click="addToCart(item.id)" class="bg-[#FF5A5F] text-white p-[10px] rounded-[4px] border-[1px] border-[#FF5A5F]
                                                            hover:bg-white hover:border-[1px] hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                                                            transition ease-in-out delay-[30ms] w-full">
                                <p>
                                    Add to cart
                                </p>

                            </button>
                        </NuxtLink>

                    </div>
                    <p class="font-[300] text-[12px] leading-[14px] text-[#484848] mt-[25px]">
                        YOU WON'T BE CHARGED YET
                    </p>

                    <p class="error w-full text-center mt-[10px]">
                        {{ error }}
                    </p>

                    <div class="row01 w-full grid grid-cols-3 gap-[10px] mt-[10px]">
                        <div class="left w-full col-span-2 flex flex-row items-start justify-start ">
                            <p class="msg ">
                                {{ msg }}
                            </p>
                        </div>
                        <div class="right w-full flex flex-row items-start justify-end ">
                            <p class="msg">
                                {{ totalPriceNoTax }}
                            </p>
                        </div>
                    </div>

                    <div class="row02 w-full grid grid-cols-3 gap-[10px] mt-[5px]">
                        <div class="left col-span-2 w-full flex flex-row items-start justify-start ">
                            <p class="msg ">
                                {{ taxTxt }}
                            </p>
                        </div>
                        <div class="right w-full flex flex-row items-start justify-end ">
                            <p class="msg ">
                                {{ tax }}
                            </p>
                        </div>
                    </div>

                    <div class="row03 w-full grid grid-cols-3 gap-[10px] mt-[5px]">
                        <div class="left col-span-2 w-full flex flex-row items-start justify-start ">
                            <p class="msg ">
                                {{ xtraFeeTxt }}
                            </p>
                        </div>
                        <div class="right w-full flex flex-row items-start justify-end ">
                            <p class="msg ">
                                {{ xtraFee }}
                            </p>
                        </div>
                    </div>

                    <div class="row04 w-full grid grid-cols-3 gap-[10px] mt-[5px]">
                        <div class="left col-span-2 w-full flex flex-row items-start justify-start ">
                            <p class="msg ">
                                {{ subTotalTxt }}
                            </p>
                        </div>
                        <div class="right w-full flex flex-row items-start justify-end ">
                            <p class="msg ">
                                {{ subTotal }}
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            <!-- <div class="w-full text-center pb-[10px]">
                <h1 class="text-center">
                    Item added to cart
                </h1>
            </div> -->

        </div>
    </div>
</template>

<script setup>
import ProductId from '~/pages/details/[productId].vue';

const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products?limit=0')
</script>

<script>
export default {
    data() {
        return {
            itemNum: 1,
            msg: '',
            totalPriceNoTax: '',
            tax: '',
            taxTxt: '',
            xtraFee: '',
            xtraFeeTxt: '',
            subTotal: '',
            subTotalTxt: '',
            error: ''
        }
    }
    ,
    methods: {
        async addToCart(prodId) {
            console.log(prodId)
            let { data: product } = await useFetch('https://dummyjson.com/products/' + prodId)
            let dataProduct = product._rawValue
            dataProduct.qty = this.itemNum
            let leStock = document.getElementById('stock').innerHTML
            console.log(dataProduct)
            if (dataProduct.qty > leStock) {
                console.log('cant do that cuh')
            } else {
                if (!localStorage.getItem("a")) {
                    console.log('aint got item with this id inside the cart pardner')
                    let array = []
                    dataProduct.cartId = 1
                    array.push(dataProduct)
                    localStorage.setItem("a", JSON.stringify(array))
                    console.log(JSON.parse(localStorage.getItem("a")))
                    console.log(dataProduct)
                    // this.cart = JSON.parse(localStorage.getItem("a"))
                    console.log('im going insane')
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
                        console.log(stuffAlreadyInside.id)
                        dataProduct.cartId = stuffAlreadyInside.length + 1
                        stuffAlreadyInside.push(dataProduct)
                        localStorage.setItem("a", JSON.stringify(stuffAlreadyInside));
                        this.cart = JSON.parse(localStorage.getItem("a"))
                        console.log(stuffAlreadyInside[10].id + ' camed');
                    } else {
                        for (let j = 0; j < stuffAlreadyInside.length; j++) {
                            console.log('shidded')
                            if (stuffAlreadyInside[j].id === prodId) {
                                let totalQty = stuffAlreadyInside[j].qty + this.itemNum
                                console.log(stuffAlreadyInside[j].stock)
                                console.log(totalQty)
                                if (totalQty <= stuffAlreadyInside[j].stock) {
                                    stuffAlreadyInside[j].qty += this.itemNum
                                } else {
                                    console.log('we run out of stock mate sorry')
                                }
                                localStorage.setItem("a", JSON.stringify(stuffAlreadyInside))
                                this.cart = JSON.parse(localStorage.getItem("a"))
                            }
                        }
                        console.log('shid and camed')
                    }
                    console.log('im going insaner')

                }
                console.log(dataProduct.id + ' cheese ' + dataProduct.qty)
            }
        }
        ,
        async count() {
            let whatId = useRoute().params
            console.log(whatId.productId)
            let { data: product } = await useFetch('https://dummyjson.com/products/' + whatId.productId)
            let prodData = product._rawValue
            let stock = prodData.stock
            console.log(prodData.price)
            let price = prodData.price
            if (this.itemNum > 0 && this.itemNum <= stock) {
                this.msg = 'Item Price : ' + '$' + price + ' x ' + this.itemNum
                let countTotalPriceNoTax = price * this.itemNum
                this.totalPriceNoTax = '$' + countTotalPriceNoTax
                let getTaxxedBaka = countTotalPriceNoTax * 10 / 100
                this.taxTxt = 'Tax : ' + '$' + this.totalPriceNoTax + ' x ' + '10%'
                this.tax = '$' + getTaxxedBaka
                let getSvcFeed = countTotalPriceNoTax * 15 / 100
                this.xtraFeeTxt = 'Service Fee : ' + '$' + this.totalPriceNoTax + ' x ' + '15%'
                this.xtraFee = '$' + getSvcFeed
                let countTotal = countTotalPriceNoTax + getTaxxedBaka + getSvcFeed
                this.subTotalTxt = 'Sub Total : '
                this.subTotal = '$' + countTotal
                this.error = ''
            } else {
                this.msg = ''
                this.totalPriceNoTax = ''
                this.tax = ''
                this.taxTxt = ''
                this.xtraFee = ''
                this.xtraFeeTxt = ''
                this.subTotal = ''
                this.subTotalTxt = ''
                this.error = 'Invalid Quantity'
            }
        }
    }
    ,
    created() {
        this.count()
    }
}
</script>

<style scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}
</style>
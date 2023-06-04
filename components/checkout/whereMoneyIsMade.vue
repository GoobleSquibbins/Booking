<template>
    <div class="w-full h-full">
        <div class="w-full mt-[65px] border-[1px] border-black rounded-[4px] sticky top-[50px]">
            <div class="w-full h-full p-[5px]">
                <div class="w-full border-b-[1px] border-black">
                    <div v-for="item in cart" class="w-full h-full grid grid-cols-4">
                        <div
                            class="w-full col-span-2 h-full font-[300] text-[14px] leading-[18px] flex items-center justify-start">
                            <p class="mr-[5px]">
                                {{ item.cartId }}.
                            </p>
                            <p>
                                {{ item.title }}
                            </p>
                        </div>
                        <div class="w-full h-full flex items-center justify-start">
                            <p>
                                Qty : {{ item.qty }}
                            </p>
                        </div>
                        <div class="w-full h-full float-right flex items-center justify-end">
                            <p class="mr-auto">
                                $
                            </p>
                            <p>
                                {{ rawTotal }}
                            </p>
                        </div>
                    </div>

                    <div class=" w-full grid grid-cols-4 h-full">
                        <div class="w-full col-span-2 h-full flex items-center justify-start">
                            total :
                        </div>
                        <div>
                            {{ totalNumberofItems }}
                        </div>
                        <div class="w-full h-full flex items-center justify-end ">
                            <p class="mr-auto">
                                $
                            </p>
                            <p>
                                {{ rawTotal }}
                            </p>
                        </div>
                    </div>
                </div>



                <div class="tax grid grid-cols-4 w-full">
                    <div class="w-full col-span-3">
                        <p>
                            10% Tax :
                        </p>
                    </div>
                    <div class="flex items-center">
                        <p class="mr-auto">
                            $
                        </p>
                        <p>
                            {{ taxxed }}
                        </p>
                    </div>
                </div>

                <div class="svcFee grid grid-cols-4 w-full">
                    <div class="w-full col-span-3">
                        <p>
                            15% Service Fee :
                        </p>
                    </div>
                    <div class="flex items-center">
                        <p class="mr-auto">
                            $
                        </p>
                        <p>
                            {{ svcFee }}
                        </p>
                    </div>
                </div>

                <div class="subTotal grid grid-cols-4 w-full">
                    <div class="w-full col-span-3">
                        <p>
                            Sub Total :
                        </p>
                    </div>
                    <div class="flex items-center">
                        <p class="mr-auto">
                            $
                        </p>
                        <p>
                            {{ subTotal }}
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            cart: '',
            rawTotal: '',
            totalNumberofItems: '',
            taxxed: '',
            svcFee: '',
            subTotal: ''
        }
    }
    ,
    methods: {
        initializeCart() {
            this.cart = JSON.parse(localStorage.getItem("a"))
        }
        ,
        count() {
            //num o items
            let arrayOfItems = JSON.parse(localStorage.getItem("a"))
            this.totalNumberofItems = arrayOfItems.length
            if (this.totalNumberofItems === 1) {
                this.totalNumberofItems = arrayOfItems.length + ' item'
            } else {
                this.totalNumberofItems = arrayOfItems.length + ' items'
            }

            //the item has entered the cart millions must pay
            let priceArray = []
            for (let i = 0; i < arrayOfItems.length; i++) {
                priceArray.push(arrayOfItems[i].price * arrayOfItems[i].qty)
                this.rawTotal = priceArray.reduce((partialSum, a) => partialSum + a, 0);
                console.log(this.rawTotal)
            }

            //the IRS
            this.taxxed = Math.ceil(this.rawTotal * 10 / 100)

            //mista krabs
            this.svcFee = Math.ceil(this.rawTotal * 15 / 100)

            //count em up bosco
            this.subTotal = this.rawTotal + this.taxxed + this.svcFee
        }
    }
    ,
    beforeMount() {
        this.initializeCart()
        this.count()
    }
}
</script>

<style lang="scss" scoped></style>
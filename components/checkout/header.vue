<template>
    <div class="md:w-[1340px] w-full md:pl-0 pl-[10px] md:pr-0 pr-[10px]">
        <div class="header w-full border-b-[1px] border-[#484848] flex flex-row items-center">
            <div class="flex flex-col">
                <h1 class="font-[700] text-[28px] leading-[32px] text-[#484848] uppercase">
                    Your shopping cart
                </h1>
                <p class=" font-[500] text-[12px] leading-[14px] text-[#767676]">
                    You have a total of {{ sum }} items in your cart
                </p>
            </div>

            <div class="ml-auto p-[5px]">
                <NuxtLink to="/seeAll">
                    <button class="
                            hover:bg-white hover:text-[#FF5A5F] transition ease-in-out delay-[30ms]
                            bg-[#FF5A5F] border-[1px] border-[#FF5A5F] text-white rounded-[50px] p-[10px]">
                        continue browsing
                    </button>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            sum: ''
        }
    },
    methods: {
        getTotalItemInACart() {
            if (!localStorage.getItem("a")) {
                this.sum = 0
            } else {
                let stuffInsideTheCart = JSON.parse(localStorage.getItem("a"))
                let array = []
                for (let i = 0; i < stuffInsideTheCart.length; i++) {
                    let qtyPerItem = stuffInsideTheCart[i].qty
                    array.push(qtyPerItem)
                }
                this.sum = array.reduce((partialSum, a) => partialSum + a, 0);

                // let totalItemsInside = stuffInsideTheCart[daIndex].cartId
                console.log(this.sum + ' cheese')
            }

        },
    }
    ,
    beforeMount() {
        this.getTotalItemInACart()
    }
}
</script>

<style lang="scss" scoped></style>
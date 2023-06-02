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
                </div>
                <div class="form w-full flex flex-col items-center">
                    <div class="guests mt-[5px] w-full">
                        <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                            Number of Items
                        </label>
                        <br>

                        <input v-model="itemNum" type="number" class="
                            w-full h-[60px] 
                            border-[1px] border-[#767676] rounded-[4px]
                            text-center text-[16px] leading-[19px]" />

                    </div>
                    <div class="submit mt-[20px] w-full">
                        <button @click="count" class="bg-[#FF5A5F] text-white p-[10px] rounded-[4px] border-[1px] border-[#FF5A5F]
                                hover:bg-white hover:border-[1px] hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                                transition ease-in-out delay-[30ms] w-full">
                            <p>
                                Add to cart
                            </p>

                        </button>
                    </div>
                    <p class="font-[300] text-[12px] leading-[14px] text-[#484848] mt-[25px]">
                        YOU WON'T BE CHARGED YET
                    </p>
                    <p class="msg w-full text-center">
                        {{ msg }}
                    </p>
                    <p id="stock" class="hidden">
                        {{ item.stock }}
                    </p>
                    <p id="price" class="hidden">
                        {{ item.price }}
                    </p>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup>
const { productId } = useRoute().params
const { data: stuff } = await useFetch('https://dummyjson.com/products')
</script>

<script>
export default {
    data() {
        return {
            itemNum: '',
            msg : ''
        }
    }
    ,
    methods: {
        count() {
            let stock = document.getElementById('stock').innerHTML
            let price = document.getElementById('price').innerHTML
            if (this.itemNum > 0 && this.itemNum <= stock) {
                this.msg = '$' + this.itemNum * price
            } else {
                this.msg = 'Invalid Quantity'
            }
        }
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
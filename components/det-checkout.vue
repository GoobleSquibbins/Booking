<template>
    <div class="h-full w-full">
        <div v-for="item in stuff.products.filter(
            function (i) { return i.id == productId })"
            class="sticky top-[100px] w-full border-[1px] border-[#767676] rounded-[10px] flex flex-col items-start">
            <div class="inside m-[30px]">
                <div class="head grid grid-cols-2 gap-10">
                    <h1 class="text-[24px] leading-[28px] font-[300] text-[#484848]">
                        $<span id="price" class="text-[24px] leading-[28px] font-[300] text-[#484848]">{{ item.price
                        }}</span> <span class="text-[16px] leading-[19px] font-[300] text-[#484848]">/ Nights</span>
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
                    <div class="dates w-full grid grid-cols-2 gap-0">
                        <div class="in">
                            <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                                Check-in
                            </label>
                            <input v-model="c_in"
                                class="focus:outline-none box-border p-[10px] text-center rounded-tl-[4px] rounded-bl-[4px] border-[1px] border-[#767676] w-[166px] h-[60px] left-0"
                                type="date" placeholder="DD/MM/YYYY">
                        </div>
                        <div class="in">
                            <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                                Check-out
                            </label>
                            <input v-model="c_out"
                                class="focus:outline-none box-border p-[10px] rounded-tr-[4px] rounded-br-[4px] border-[1px] border-[#767676] w-[166px] h-[60px] left-0"
                                type="date">
                        </div>
                    </div>
                    <div class="guests mt-[5px]">
                        <label class="text-[13px] font-thin leading-[16px] uppercase text-[#484848]">
                            Number of Guests
                        </label>
                        <br>
                        <input v-model="guests" type="number"
                            class="focus:outline-none
                                            text-[30px] pl-[30px] w-full h-[60px] border-[1px] border-[#767676] rounded-[4px]">
                    </div>
                    <div class="submit mt-[20px] float-right">
                        <button @click.prevent="dino" class="bg-[#FF5A5F] text-white p-[10px] rounded-[4px] border-[1px] border-[#FF5A5F]
                                            hover:bg-white hover:border-[1px] hover:border-[#FF5A5F] hover:text-[#FF5A5F]
                                            transition ease-in-out delay-[30ms]">
                            CHECK
                        </button>
                    </div>
                    <p class="font-[300] text-[12px] leading-[14px] text-[#484848] mt-[25px]">
                        YOU WON'T BE CHARGED YET
                    </p>
                    <div class="msg w-[70%] flex flex-col items-start mt-[10px] text-[14px] leading-[18px] font-[300] text-[#484848]">
                        <p class="m-[5px]">
                            {{ row01 }}
                        </p>
                        <p class="m-[5px]">
                            {{ row02 }}
                        </p>
                        <p class="m-[5px]">
                            {{ row03 }}
                        </p>
                        <p class="m-[5px]">
                            {{ rowScrt }}
                        </p>
                        <p class="m-[5px]">
                            {{ row04 }}
                        </p>
                    </div>

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
            c_in: '',
            c_out: '',
            guests: '',
            payUp: '',
            total: '',
            row01: '',
            row02: '',
            row03: '',
            row04: '',
            rowScrt: ''
        }
    }
    ,
    methods: {
        dino() {
            let harga = document.getElementById('price').innerHTML

            let dateIn = new Date(this.c_in)
            let dateOut = new Date(this.c_out)

            let selisih = dateOut.getTime() - dateIn.getTime()
            let totalDif = Math.ceil(selisih / (1000 * 3600 * 24))

            if (totalDif > 0) {
                if (this.guests == 1) {
                    this.payUp = totalDif * harga
                    this.row01 = '$' + harga + ' x ' + totalDif + ' Days' + ' : ' + '$' + this.payUp

                    let tax = this.payUp * 10 / 100

                    let svcFee = this.payUp * 15 / 100
                    this.rowScrt = 'Total Guests : ' + this.guests
                    this.row02 = 'Tax : ' + '$' + tax
                    this.row03 = 'Service Fee : ' + '$' + svcFee
                    this.row04 = 'Total Payment : ' + '$' + Math.ceil(this.payUp + tax + svcFee)
                } else if (this.guests > 1) {
                    let guestXtra = parseInt(this.guests) * 50
                    this.payUp = totalDif * harga
                    this.row01 = '$' + harga + ' x ' + totalDif + ' Days' + ' = ' + '$' + this.payUp

                    this.rowScrt = 'Total Guests : ' + this.guests + ', Extra Fee : ' + '$' + guestXtra

                    let tax = this.payUp * 10 / 100

                    let svcFee = this.payUp * 15 / 100

                    this.row02 = 'Tax : ' + '$' + tax
                    this.row03 = 'Service Fee : ' + '$' + guestXtra
                    this.row04 = 'Total Payment : ' + '$' + Math.ceil(this.payUp + tax + svcFee + guestXtra)
                } else {
                    this.row01 = 'Invalid Input'
                }
            } else {
                this.row01 = 'Invalid Input'
            }


            // let harga = document.getElementById('price').innerHTML

            // let c_in = new Date(this.c_in)
            // let c_out = new Date(this.c_out)
            // let selisih = c_out.getTime() - c_in.getTime()
            // let totalDif = Math.ceil(selisih / (1000 * 3600 * 24))
            // console.log(guest)
            // if (totalDif > 0) {
            //     if (this.guestNum == 1) {
            //         this.payUp = guest + (totalDif * harga)
            //         this.row01 = '$' + harga + ' x ' + totalDif + ' Hari'
            //         this.row02 = 'Total : ' + guest
            //         console.log('$' + this.payUp + ' Days: ' + totalDif + ' ' )
            //     } else if(this.guestNum !== 1 && this.guestNum > 0){
            //         this.payUp = (totalDif * harga) + guest
            //         let svcFee = this.payUp + (this.payUp * 15 / 100)
            //         let tax = this.payUp + (this.payUp * 10 /100)
            //         this.row01 = '$' + harga + ' x ' + totalDif + ' Hari'
            //         this.row02 = 'Total : ' + guest
            //         console.log(this.row01)
            //         this.total = 'Total Price : ' + '$' + (this.payUp + svcFee + tax)
            //     }
            //     else{
            //         this.payUp = 'error'
            //         console.log('error')
            //     }
            // }
            // else {
            //     this.payUp = 'error'
            //     console.log('error')
            // }

        }


    }
}
</script>

<style scoped></style>
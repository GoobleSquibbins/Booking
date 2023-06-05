<template>
    <div class="w-full h-full relative">
        <div class="w-full mt-[65px] sticky top-[50px]">
            <div class="w-full h-full p-[5px] border-[1px] border-black rounded-[4px]">
                <div class="w-full border-b-[1px] border-black">
                    <div v-for="item in cart" class="w-full h-full grid grid-cols-4">
                        <div
                            class="w-full col-span-2 h-full font-[300] text-[14px] leading-[18px] flex items-center justify-start">
                            <p class="mr-[5px]">
                                {{ item.cartId }}.
                            </p>
                            <p class="font-[400] text-[15px] leading-[17px]">
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
                                {{ item.price * item.qty }}
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
            <div class="w-full">
                <div id="login_form"
                    class="login_form flex flex-col items-start p-[10px] justify-center w-full mt-[10px] border-[1px] rounded-[4px] border-black">
                    <h1 class="font-[500] text-[16px] leading-[19px]">
                        LOGIN TO FINISH TRANSACTION
                    </h1>
                    <div class="flex flex-col items-start w-full mt-[10px]">
                        <label class="font-[400] text-[14px] leading-[16px]">USERNAME</label>
                        <input v-model="username" type="text"
                            class="mt-[5px] w-full h-[50px] border-[1px] border-[#767676] rounded-[4px] focus:outline-none p-[10px]">
                    </div>
                    <div class="flex flex-col items-start w-full mt-[10px]">
                        <label class="font-[400] text-[14px] leading-[16px]">PASSWORD</label>
                        <input v-model="password" type="text"
                            class="mt-[5px] w-full h-[50px] border-[1px] border-[#767676] rounded-[4px] focus:outline-none p-[10px]">
                    </div>
                    <div class="flex flex-col items-start w-full mt-[10px]">
                        <button @click="login"
                            class="w-full border-[1px] border-[#FF5A5F] bg-[#FF5A5F] p-[5px] rounded-[4px] text-white hover:bg-white hover:text-[#FF5A5F] transition ease-in-out delay-[30ms]">
                            <h1 class="font-[500] text-[16px] leading-[21px]">
                                LOGIN
                            </h1>
                        </button>
                    </div>
                </div>
            </div>
            <div id="smbt_order" class="submit_order w-full mt-[10px] hidden">
                <button @click="order"
                    class=" w-full h-[40px] border-[1px] border-[#FF5A5F] hover:text-[#FF5A5F] hover:bg-white transition ease-in-out delay-[30ms] rounded-[4px] text-white bg-[#FF5A5F]">
                    <h1 class="font-[500] text-[16px] leading-[21px]">
                        ORDER
                    </h1>
                </button>
            </div>
        </div>
        <div id="msgSccss"
            class="hidden absolute flex-col items-center w-[500px] bg-white border-[1px] p-[10px] border-black left-[-420px] top-[10px] shadow-2xl rounded-[12px]">
            <div class="flex w-full items-center relative justify-center">
                <h1>
                    ORDER SUCCESS
                </h1>
                <button @click="close()" class="absolute top-0 right-0 text-[#484848] hover:text-black">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                        stroke="currentColor" class="w-7 h-7">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
            <div class="w-full flex items-center justify-center">
                <img class="h-[300px] w-[300px]" src="https://media.istockphoto.com/id/490988025/id/foto/muda-bahagia-positif-remaja-pria-gesturing-ok.jpg?s=1024x1024&w=is&k=20&c=X5hob1qoslwN7tvBcyxVd0VjHOWc9BAA0EmwKyMNh4g=" alt="">
            </div>
            <div class="w-[50%] mt-[10px]">
                <p>
                    We will send your order of items right at your doorstep, just don't ask how we know your address...
                </p>
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
            subTotal: '',
            username: '',
            password: ''
        }
    }
    ,
    methods: {
        close(){
            localStorage.removeItem("a")
            window.location.href = "/seeAll"
        }
        ,
        order(){
            document.getElementById('msgSccss').style.display = "flex";
        }
        ,
        checkLoginStat() {
            if (!localStorage.getItem("login")) {
                document.getElementById('login_form').style.display = "flex";
            } else {
                document.getElementById('login_form').style.display = "none";
                document.getElementById('smbt_order').style.display = "block";
            }
        }
        ,
        login() {
            document.getElementById('login_form').style.display = "none";
            document.getElementById('smbt_order').style.display = "block";
        }
        ,
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
        this.checkLoginStat()
    }
}
</script>

<style lang="scss" scoped></style>
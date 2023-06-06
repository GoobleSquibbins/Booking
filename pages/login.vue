<template>
    <div id="form" class="w-full flex flex-col items-center mt-[112px]">
        <div class="md:w-[500px] w-[300px] border-[1px] border-black rounded-[12px] bg-white flex flex-col items-center">
            <div class="p-[10px] w-full">
                <h1 class="text-center font-[400] text-[24px] leading-[28px] w-full">
                    LOGIN
                </h1>
                <div class="username w-full flex flex-col items-start">
                    <label class="w-full">
                        <h1 class="font-[400] text-[16px] leading-[19px]">
                            USERNAME
                        </h1>
                    </label>
                    <input type="text" v-model="username" class="w-full h-[50px] p-[10px] focus:outline-none border-[1px] border-[#767676] mt-[5px] rounded-[4px]">
                </div>
                <div class="password w-full flex flex-col items-start mt-[10px]">
                    <label class="w-full">
                        <h1 class="font-[400] text-[16px] leading-[19px]">
                            PASSWORD
                        </h1>
                    </label>
                    <input type="password" v-model="password" class="w-full h-[50px] p-[10px] focus:outline-none border-[1px] border-[#767676] mt-[5px] rounded-[4px]">
                </div>
                <div class="w-full">
                    <button @click="login()" class="w-full hover:bg-white hover:text-[#FF5A5F] transition ease-in-out delay-[30ms] bg-[#FF5A5F] border-[1px] border-[#FF5A5F] text-white mt-[10px] p-[5px] rounded-[4px]">
                        <h1>
                            LOGIN
                        </h1>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            username:'',
            password:''
        }
    }
    ,
    methods:{
        login(){
            console.log(this.username)
            console.log(this.password)
            
            localStorage.setItem("login", 1 )
            window.location.href = "/seeAll"
        }
        ,
        render(){
            let height =  screen.height * 0.5
            document.getElementById('form').style.marginTop = height
            console.log(height)
        }
    }
    
}
</script>

<style lang="scss" scoped></style>
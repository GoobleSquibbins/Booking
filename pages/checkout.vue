<template>
    <div class="w-full flex flex-col items-center">
        <CheckoutHeader />
        <div class="grid grid-cols-3 gap-[16px] w-[1208px]">
            <div class="col-span-2 w-full">
                <CheckoutListsOfItems />
            </div>
            <div>
                <CheckoutWhereMoneyIsMade/>
            </div>
        </div>

    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped></style>
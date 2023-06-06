<template>
    <div class="w-full flex flex-col items-center">
        <CheckoutHeader />
        <div class="grid grid-cols-3 gap-[16px] md:w-[1340px] w-full h-[720px]">
            <div class="col-span-2 w-full">
                <CheckoutListsOfItems />
            </div>
            <div class="md:pr-0 pr-[10px]">
                <CheckoutWhereMoneyIsMade/>
            </div>
        </div>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped></style>
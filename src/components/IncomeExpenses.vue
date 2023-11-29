<template>
    <div class="flex items-center flex-row justify-center bg-slate-200 mt-2 mb-6">
        <div 
        class="py-3 px-8 flex items-center flex-col justify-center w-30 
        border-solid border-r-2 border-sky-50 shadow-sm">
            <h4>Income</h4>
            <p id="money-plus" class="text-green-600">+${{ income }}</p>
        </div>
        <div class="py-3 px-8 flex items-center flex-col justify-center w-30">
            <h4>Expense</h4>
            <p id="money-minus" class="text-red-600">-${{ expense }}</p>
        </div>
    </div>
</template>

<script lang="ts" setup >
const props = defineProps({
    income: {
        type: String,
        required: true, 
    },
    expense: {
        type: String,
        required: true, 
    }
})
</script>
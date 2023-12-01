<template>
     <h3 class="font-semibold mt-6 border-solid border-b-2 border-slate-300">Add new transaction</h3>
    <form 
    id="form" 
    class="flex items-start justify-center flex-col gap-2 w-full"
    @submit.prevent="onSubmit" >
        <div class="flex items-start justify-center flex-col gap-2 w-full">
            <label 
            for="text"
            class="font-semibold mt-2 text-base">
            Income/Expense
            </label>
            <input 
            type="text" 
            id="text" 
            placeholder="Enter text..."
            class="px-2 py-1 w-full text-base"
            v-model="text"/>
        </div>
        <div class="flex items-start justify-center flex-col gap-2 w-full">
            <label 
            for="amount"
            class="font-semibold text-base">
            Amount 
            </label>
            <input
            type="amount"
            id="amount"
            placeholder="Enter amount..."
            class="px-2 py-1 w-full text-base"
            v-model="amount"/>
        </div>
        <button class="bg-purple-600 text-white text-base rounded hover:bg-purple-300 mt-4 px-2 py-1 w-full duration-300 shadow-sm hover:w-4/5 m-auto">Add transaction</button>
    </form>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const text = ref('');
const amount = ref('');
const emit = defineEmits(['transactionSubmited']);
const toast = useToast();

const onSubmit = () => {
    if(!text.value || !amount.value) {
    toast.error('Both fields must br filled');
    return;
    }
    
    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value),
    }

    emit('transactionSubmited', transactionData);

    text.value = '';
    amount.value = '';
};
</script>
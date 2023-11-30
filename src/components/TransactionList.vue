<template>
    <h3 class="font-semibold border-solid border-b-2 border-slate-300">History</h3>
    <ul id="list" class="duration-300">
      <li 
      v-for="transaction in transactions"
      v-bind:key="transaction.id"
      class="relative bg-slate-200 mt-2 px-2 py-1 flex items-center text-base
            flex-row justify-between shadow-sm border-solid border-r-4  duration-300"
            @mouseover="showButton = true"
      :class="transaction.amount < 0 ? 'border-red-600' : 'border-green-600'">
          <button 
          class="hidden bg-red-600 px-2 text-white duration-300" 
          v-show="showButton" 
          @mouseover.stop
          @click="deleteTransaction(transaction.id)"> 
          x
          </button>
           {{ transaction.text }} <span>${{ transaction.amount }}</span>
      </li>  
    </ul>
  </template>
  
  <script lang="ts" setup>
  import { ref } from 'vue';

  const emit = defineEmits(['transationDeleted'])

  const showButton = ref(false);
  const props = defineProps({
    transactions: {
      type: Array<{
        id: number;
        text: string;
        amount: number;
      }>,
      required: true,
    }
  })

  const deleteTransaction = (id: number) => {
    emit('transationDeleted', id)
  }
  </script>
  
  <style scoped>
  li:hover .hidden {
    display: flex;
  }
  </style>
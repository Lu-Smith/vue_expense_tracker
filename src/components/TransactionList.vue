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
          v-show="showButton" @mouseover.stop> 
          x
          </button>
           {{ transaction.text }} <span>${{ transaction.amount }}</span>
      </li>  
      <!-- </li>
      <li
        class="relative bg-slate-200 mt-2 px-2 py-1 flex items-center text-base
          flex-row justify-between shadow-sm border-solid border-r-4 border-green-600 duration-300"
        @mouseover="showButton = true"
    
      > -->
      <!-- <button class="hidden bg-red-600 px-2 text-white duration-300" v-show="showButton" @mouseover.stop>
          x
      </button> -->
        <!-- Income <span>$800</span> -->
      <!-- </li> -->
    </ul>
  </template>
  
  <script lang="ts">
  export default {
    data() {
      return {
        showButton: false,
        transactions: [
        {id: 1, text: 'Flowers', amount: -19.99},
        {id: 2, text: 'Bread', amount: -3.40},
        {id: 3, text: 'Milk', amount: -1.30},
        {id: 4, text: 'Salary', amount: 199.99},      ]
      };
    },
  };
  </script>
  
  <style scoped>
  li:hover .hidden {
    display: flex;
  }
  </style>
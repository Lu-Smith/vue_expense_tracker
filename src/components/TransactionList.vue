<template>
    <h3 class="font-semibold border-solid border-b-2 border-slate-300">History</h3>
    <ul id="list" class="duration-300">
      <li
        class="relative bg-slate-200 mt-2 px-2 py-1 flex items-center text-base
          flex-row justify-between shadow-sm border-solid border-r-4 border-red-600 duration-300"
        @mouseover="showButton = true"
      >
      <button class="hidden bg-red-600 px-2 text-white duration-300" v-show="showButton" @mouseover.stop> <!-- Use @mouseover.stop to prevent event propagation -->
          x
        </button>
        Cash <span>-$120</span>
      </li>
      <li
        class="relative bg-slate-200 mt-2 px-2 py-1 flex items-center text-base
          flex-row justify-between shadow-sm border-solid border-r-4 border-green-600 duration-300"
        @mouseover="showButton = true"
    
      >
      <button class="hidden bg-red-600 px-2 text-white duration-300" v-show="showButton" @mouseover.stop>
          x
        </button>
        Income <span>$800</span>
   
      </li>
    </ul>
  </template>
  
  <script lang="ts">
  export default {
    data() {
      return {
        showButton: false,
      };
    },
  };
  </script>
  
  <style scoped>
  li:hover .hidden {
    display: flex;
  }
  </style>
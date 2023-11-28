<template>
    <h3 class="font-semibold border-solid border-b-2 border-slate-300">History</h3>
    <ul id="list" class="list">
      <li
        class="relative bg-slate-200 mt-2 px-2 py-1 flex items-center 
          flex-row justify-between shadow-sm border-solid border-r-4 border-red-600"
        @mouseover="showButton = true"
        @mouseleave="showButton = false"
      >
        Cash <span>-$120</span>
        <button class="hidden absolute bg-red-600 px-2 text-white duration-300" v-show="showButton" @mouseover.stop> <!-- Use @mouseover.stop to prevent event propagation -->
          x
        </button>
      </li>
      <li
        class="relative bg-slate-200 mt-2 px-2 py-1 flex items-center 
          flex-row justify-between shadow-sm border-solid border-r-4 border-green-600"
        @mouseover="showButton = true"
        @mouseleave="showButton = false"
      >
        Income <span>$800</span>
        <button class="hidden absolute bg-red-600 px-2 text-white duration-300" v-show="showButton" @mouseover.stop>
          x
        </button>
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
    margin-left: -35px;
  }
  </style>
<template>
  <div 
  class="w-full p-7 bg-slate-50 flex items-center flex-col justify-start">
    <Header />
    <div class="container w-96">
      <Balance />
      <IncomeExpenses />
      <TransactionList />
    </div>
  </div>
</template>

<script lang="ts">
 import Header from './components/Header.vue';
 import Balance from './components/Balance.vue';
 import IncomeExpenses from './components/IncomeExpenses.vue';
 import TransactionList from './components/TransactionList.vue';

 export default {
  components: {
    Header,
    Balance,
    IncomeExpenses,
    TransactionList
  }
 }
</script>

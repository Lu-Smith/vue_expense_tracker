<template>
  <div 
  class="w-full p-7 bg-slate-50 flex items-start flex-col justify-center">
    <Header />
    <div class="">
      <Balance />
      <IncomeExpenses />
      <TransactionList />
      <AddTransactions />
    </div>
  </div>
</template>

<script lang="ts">
 import Header from './components/Header.vue';
 import Balance from './components/Balance.vue';
 import IncomeExpenses from './components/IncomeExpenses.vue';
 import TransactionList from './components/TransactionList.vue';
 import AddTransactions from './components/AddTransactions.vue';

 export default {
  components: {
    Header,
    Balance,
    IncomeExpenses,
    TransactionList,
    AddTransactions
  }
 }
</script>

<template>
  <div 
  class="w-full p-7 bg-slate-50 flex items-start flex-col justify-center">
    <Header />
    <div class="">
      <Balance :total="total" />
      <IncomeExpenses :income="income"/>
      <TransactionList :transactions="transactions"/>
      <AddTransactions />
    </div>
  </div>
</template>

<script lang="ts" setup>
 import Header from './components/Header.vue';
 import Balance from './components/Balance.vue';
 import IncomeExpenses from './components/IncomeExpenses.vue';
 import TransactionList from './components/TransactionList.vue';
 import AddTransactions from './components/AddTransactions.vue';

 import { ref, computed } from 'vue';

 const transactions = ref([
  {id: 1, text: 'Flowers', amount: -19.99},
  {id: 2, text: 'Bread', amount: -2.40},
  {id: 3, text: 'Milk', amount: -1.30},
  {id: 4, text: 'Salary', amount: 799.99}]);

  const total = computed(() => {
    return transactions.value.reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0)
  });

  const income = computed(() => {
    return transactions.value
    .filter(() => transactions.value.amount > 0)
    .reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0).toFixed(2);
  });
  
  const expense = computed(() => {
    return transactions.value
    .filter(() => {transactions.value.amount < 0})
    .reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0).toFixed(2);
  });
</script>

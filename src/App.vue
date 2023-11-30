<template>
  <div 
  class="w-full p-7 bg-slate-50 flex items-start flex-col justify-center">
    <Header />
    <div class="">
      <Balance :total="total" />
      <IncomeExpenses :income="income" :expense="expense"/>
      <TransactionList :transactions="transactions" @transation-deleted="handleTransactionDeleted"/>
      <AddTransactions @transaction-submited="handleTransactionSubmitted"/>
    </div>
  </div>
</template>

<script lang="ts" setup>
 import Header from './components/Header.vue';
 import Balance from './components/Balance.vue';
 import IncomeExpenses from './components/IncomeExpenses.vue';
 import TransactionList from './components/TransactionList.vue';
 import AddTransactions from './components/AddTransactions.vue';

 import { useToast } from 'vue-toastification';

 interface dataProps {
  id: number,
  text: string,
  amount: number,
 }

 import { ref, computed } from 'vue';

 const toast = useToast();

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
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0).toFixed(2);
  });
  
  const expense = computed(() => {
    return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0).toFixed(2);
  });

  const handleTransactionSubmitted = (transactionData: dataProps) => {
    transactions.value.push({
      id: generateUniqueId(),
      text: transactionData.text,
      amount: transactionData.amount,
    });

    toast.success('Transaction added');
  };

  const generateUniqueId = () => {
    return Math.floor(Math.random() * 1000000);
  };

  const handleTransactionDeleted = (id: number) => {
    transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  console.log(id);
  toast.success('Transaction deleted');
  
  }
</script>

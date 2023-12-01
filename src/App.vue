<template>
  <div 
  class="w-full p-7 rounded bg-slate-50 flex items-start flex-col justify-center">
    <Header />
    <div class="">
      <Balance :total="total" />
      <IncomeExpenses :income="income" :expense="expense"/>
      <TransactionList :transactions="transactions" @transaction-deleted="handleTransactionDeleted"/>
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

 interface DataProps {
  id: number,
  text: string,
  amount: number,
 }

 import { ref, computed, onMounted } from 'vue';

 const toast = useToast();

 const transactions = ref<DataProps[]>([]);

 onMounted(() => {
  const savedTransactions = JSON.parse
  (localStorage.getItem('transactions') || 'null') as DataProps[];
  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});

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

  const handleTransactionSubmitted = (transactionData: DataProps) => {
    transactions.value.push({
      id: generateUniqueId(),
      text: transactionData.text,
      amount: transactionData.amount,
    });

    saveTransactionsToLocalStorage();

    toast.success('Transaction added');
  };

  const generateUniqueId = () => {
    return Math.floor(Math.random() * 1000000);
  };

  const handleTransactionDeleted = (id: number) => {
    transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  saveTransactionsToLocalStorage;

  toast.success('Transaction deleted');
  }

  const saveTransactionsToLocalStorage = () => {
    localStorage.setItem('transactions', JSON.stringify(
      transactions.value
    ));
  }
</script>

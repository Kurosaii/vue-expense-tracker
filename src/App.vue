<script setup>
import { v4 as uuidv4 } from 'uuid';
import { computed, onMounted, ref } from 'vue';
import { useToast } from 'vue-toastification';

import AddTransaction from './components/AddTransaction.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TheBalance from './components/TheBalance.vue';
import TheHeader from './components/TheHeader.vue';
import TransactionList from './components/TransactionList.vue';

const toast = useToast();

const transactions = ref([]);

const total = computed(() => income.value + expenses.value);

const income = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0));

const expenses = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0));

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem('transactions'));

  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});

function handleTransactionSubmitted(transactionData) {
  const { title, amount } = transactionData;

  transactions.value.push({
    id: uuidv4(),
    title,
    amount,
  });

  saveTransactionsToLocalStorage();

  toast.success('Transaction added');
}

function handleTranslationDeleted(transactionId) {
  transactions.value = transactions.value.filter((transaction) => transaction.id != transactionId);

  saveTransactionsToLocalStorage();

  toast.success('Transaction deleted');
}

function saveTransactionsToLocalStorage() {
  localStorage.setItem('transactions', JSON.stringify(transactions.value));
}
</script>

<template>
  <TheHeader />

  <div class="container">
    <TheBalance :total="total.toFixed(2)" />
    <IncomeExpenses
      :expenses="expenses.toFixed(2)"
      :income="income.toFixed(2)"
    />
    <TransactionList
      :transactions
      @transactionDeleted="handleTranslationDeleted"
    />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </div>
</template>
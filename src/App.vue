<script setup>
import { v4 as uuidv4 } from 'uuid';
import { computed, ref } from 'vue';
import { useToast } from 'vue-toastification';

import AddTransaction from './components/AddTransaction.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TheBalance from './components/TheBalance.vue';
import TheHeader from './components/TheHeader.vue';
import TransactionList from './components/TransactionList.vue';

const toast = useToast();

const transactions = ref([
  {
    id: 1,
    title: 'Flower',
    amount: -19.99,
  },
  {
    id: 2,
    title: 'Salary',
    amount: 299.97,
  },
  {
    id: 3,
    title: 'Book',
    amount: -10,
  },
  {
    id: 4,
    title: 'Camera',
    amount: 150,
  },
]);

const total = computed(() => income.value + expenses.value);

const income = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0));

const expenses = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => acc + transaction.amount, 0));

function handleTransactionSubmitted(transactionData) {
  const { title, amount } = transactionData;

  transactions.value.push({
    id: uuidv4(),
    title,
    amount,
  });

  toast.success('Transaction added');
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
    <TransactionList :transactions />
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </div>
</template>
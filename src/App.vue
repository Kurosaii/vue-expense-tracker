<script setup>
import { ref } from 'vue';

import AddTransaction from './components/AddTransaction.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TheBalance from './components/TheBalance.vue';
import TheHeader from './components/TheHeader.vue';
import TransactionList from './components/TransactionList.vue';

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
</script>

<template>
  <TheHeader />

  <div class="container">
    <TheBalance />
    <IncomeExpenses />
    <TransactionList :transactions />
    <AddTransaction />
  </div>
</template>
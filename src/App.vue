<script setup>
import AddTransaction from './components/AddTransaction.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TheBalance from './components/TheBalance.vue';
import TheHeader from './components/TheHeader.vue';
import TransactionList from './components/TransactionList.vue';
</script>

<template>
  <TheHeader />

  <div class="container">
    <TheBalance />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </div>
</template>
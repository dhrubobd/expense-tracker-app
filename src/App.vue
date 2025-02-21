<script setup>
import { ref,computed,reactive } from 'vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';

const transactions = reactive([
  { title: 'Salary', amount: 5000, type: 'income' },
  { title: 'Rent', amount: 1000, type: 'expense' },
  { title: 'Food', amount: 200, type: 'expense' },
  { title: 'Transport', amount: 50, type: 'expense' },
]);

</script>

<template>
  <div>
    <h1>Simple Expense Tracker Apps</h1>
  </div>
  <div>
    <TransactionList :transactions="transactions"/>
  </div>
</template>

<style scoped>

</style>

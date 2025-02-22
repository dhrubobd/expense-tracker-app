<script setup>
import { ref,computed,reactive } from 'vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
const transactions=ref([]);
const storedTransactions = localStorage.getItem('transactions');
if (storedTransactions) {
        transactions.value = JSON.parse(storedTransactions);
  }

const deleteTransaction = (index) => {
      transactions.value.splice(index, 1);
      localStorage.setItem('transactions', JSON.stringify(transactions.value));
    };
</script>

<template>
  <div>
    <h1>Simple Expense Tracker Apps</h1>
    {{ transactions }}
  </div>
  <div>
    <AddTransaction :transactions="transactions"/>
  </div>
  <div>
    <TransactionList :transactions="transactions" @delete-transaction="deleteTransaction"/>
  </div>
</template>

<style scoped>

</style>

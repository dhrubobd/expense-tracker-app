<script setup>
import { reactive } from 'vue';
const props = defineProps(['transactions']);
const transaction = {
  title: '',
  amount: '',
  type: ''
};
const addTransaction = () => {
    alert(JSON.stringify(transaction));

    props.transactions.push({
        title: transaction.title,
        amount: transaction.amount,
        type: transaction.type
    });
    
    localStorage.setItem('transactions', JSON.stringify(props.transactions));
    
};
</script>

<template>
  <div  class="mt-3 row">
    <div class="mb-3 col-md-3">
      <label>Title:</label>
      <input v-model="transaction.title" class="form-control" type="text" required />
    </div>
    <div class="mb-3 col-md-3">
      <label>Amount:</label>
      <input v-model.number="transaction.amount" class="form-control" type="number" min="1" required />
    </div>
    <div class="mb-3 col-md-3">
      <label>Type:</label>
      <select v-model="transaction.type" class="form-control" required>
        <option value="INCOME">Income</option>
        <option value="EXPENSE">Expense</option>
      </select>
    </div>
    <div class="mb-3 col-md-3">
        <label>&nbsp;</label>
        <button class="btn btn-primary" @click="addTransaction">Add</button>
    </div>
  </div>
</template>

<style scoped>

</style>
<script setup>
import { ref } from 'vue';
    const props = defineProps(['transactions']);
    const amountClass = (transaction) => {
        return transaction.type === 'income' ? 'text-success' : 'text-danger';
    }
    const typeClass = (transaction) => {
        return transaction.type === 'income' ? 'text-success' : 'text-danger';
    }
</script>

<template>
    <div>
        <table class="table table-bordered mt-3" v-if="props.transactions.length">
        <thead>
            <tr>
            <th>Title</th>
            <th>Amount</th>
            <th>Type</th>
            <th>Action</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(transaction, index) in props.transactions" :key="index">
            <td>{{ transaction.title }}</td>
            <td :class="amountClass(transaction)">${{ transaction.amount }}</td>
            <td :class="typeClass(transaction)">{{ transaction.type }}</td>
            <td><button @click="$emit('deleteTransaction', index)"  class="btn btn-danger">Delete</button></td>
            </tr>
        </tbody>
        </table>
        <p v-else  class="text-center">No transactions recorded yet.</p>
     </div>
</template>

<style scoped>

</style>


<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps(['transactions']);
const emit = defineEmits(['deleteTransaction']);

const deleteTransaction = (id) => {
  emit('deleteTransaction', id);
};
</script>

<template>
  <table class="table table-dark">
    <thead>
      <tr>
        <th>Title</th>
        <th>Amount</th>
        <th>Type</th>
        <th>Action</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="transaction in transactions" :key="transaction.id">
        <td>{{ transaction.title }}</td>

       
        <td :class="transaction.type === 'EXPENSE' ? 'text-danger' : 'text-success'">
          ${{ transaction.amount }}
        </td>
        <td>{{ transaction.type }}</td>
        <td>
          <button @click="deleteTransaction(transaction.id)" class="btn btn-danger">Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>



<style scoped>
</style>

<template>
  <Header/>
  <div class="container">
    <Balance :total= "total"/>
    <IncomeExpense
      :income="income"
      :expenses="expenses"
    />
    <TransactionList
      :transactions="transactions"
    />
    <NewTransaction/>
  </div>
</template>

<style scoped>

</style>
<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import TransactionList from './components/TransactionList.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import NewTransaction from './components/NewTransaction.vue';
import { computed, ref } from 'vue';

const transactions  = ref([
    {id:0, text: 'Food', amount: -15.45},
    {id:1, text: 'Taxi', amount: -9.25},
    {id:2, text: 'Salary', amount: 988},
    {id:3, text: 'YouTube Premiunm', amount: -19.99},
    {id:4, text: 'Grosery', amount: -24.45},
 ]);

function calc (arr, transaction) {
  return arr.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2)
}

 const total = computed(() => {
  return calc(transactions.value,transaction)
 });

 const income = computed(() => {
  return transactions.value
  .filter(() => transaction.amount > 0)
  .reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2)
 });
 
 const expenses = computed(() => {
  return transactions.value
  .filter(() => transaction.amount < 0)
  .reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2)
 });

</script>

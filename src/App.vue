<template>
  <Header/>
  <div class="container">
    <Balance/>
    <IncomeExpense/>
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
 ]);

 const total = computed(() => {
  return transactions
 });

</script>

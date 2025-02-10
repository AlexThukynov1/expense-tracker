<template>
  <Header/>
  <div class="container">
    <Balance/>
    <IncomeExpense/>
    <TransactionList/>
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

//  export default {
//   components: {
//     Header,
//     Balance,
//     TransactionList,
//     IncomeExpense,
//   },
//   setup() {

//   }
//  }
</script>

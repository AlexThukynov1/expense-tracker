<template>
  <Header/>
  <div class="container">
    <Balance :total= "total"/>
    <IncomeExpense
      :income="+income"
      :expenses="+expenses"
    />
    <TransactionList
      :transactions="transactions"
      @transactionDelete = "handleTranactionDelete"/>
      
    <NewTransaction @transactionsSubmitted="handleTransactionSubmitted"  />
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
import { useToast } from 'vue-toastification';

const toast = useToast()

const transactions  = ref([
    {id:0, text: 'Food', amount: -15.45},
    {id:1, text: 'Taxi', amount: -9.25},
    {id:2, text: 'Salary', amount: 988},
    {id:3, text: 'YouTube Premiunm', amount: -19.99},
    {id:4, text: 'Grosery', amount: -24.45},
 ]);
 


 const total = computed(() => {
  return transactions.value
  .reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2)
 })

 const income = computed(() => {
  return transactions.value.filter((transaction) => transaction.amount > 0).reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2)
 });
 
 const expenses = computed(() => {
  return transactions.value
  .filter((transaction) => transaction.amount < 0)
  .reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0)
  .toFixed(2)
 });

const handleTransactionSubmitted = function (transActionsData) {
  transactions.value.push({
    id: generateUniqueId(),
    text: transActionsData.text,
    amount: transActionsData.amount
  })
  toast.success('Transaction added')

}
const generateUniqueId = function () {
  return Math.floor(Math.random() * 100000);
}
const handleTranactionDelete = function (id) {
  transactions.value = transactions.value.filter((transaction) => transaction.id !== id);

  toast.success('Transaction deleted')
}
</script>

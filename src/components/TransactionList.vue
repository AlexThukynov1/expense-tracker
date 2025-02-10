<template>
    <h2>History</h2>
    <ul id="list" class="list">
        <li v-for="transaction in transactions" :key="transaction.id">
        {{ transaction.text }}<span>{{transaction.amount}}</span><button class="delete-btn">x</button>
        </li>
        <!-- <li class="minus">Cash<span>-400</span><button class="delete-btn">x</button></li>
        <li class="plus">Paycheck<span>+400</span><button class="delete-btn">x</button></li> -->
    </ul>
</template>

<script setup>
import { ref } from 'vue';

 const transactions  = ref([
    {id:0, text: 'Food', amount: -15.45},
    {id:1, text: 'Taxi', amount: -9.25},
    {id:2, text: 'Salary', amount: 988},
    {id:3, text: 'YouTube Premiunm', amount: -19.99},
 ])
</script>

<style lang="scss" scoped>

</style>
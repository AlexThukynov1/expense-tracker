<template>
    <h2>History</h2>
    <ul id="list" class="list">
        <li v-for="transaction in transactions" :class="transaction.amount < 0? 'minus' : 'plus'" :key="transaction.id">
        {{ transaction.text }}<span>$ {{transaction.amount}}</span><button class="delete-btn">x</button>
        </li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps(['transactions'])
</script>

<style lang="scss" scoped>

</style>
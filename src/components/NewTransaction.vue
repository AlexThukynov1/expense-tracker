<template>
<h3>Add new transition</h3>
<form action="" id="form" @submit.prevent="onSubmit">
    <div class="form-control">
        <label for="text">Text</label>
        <input type="text" name="" v-model="text" id="text" placeholder="Enter text...">
    </div>
    <div class="form-control">
        <label for="amount">Amount <br>(negative - expense, positive - income)</label>
        <input type="text" name="" v-model="amount" id="amount" placeholder="Enter amount...">
    </div>
    <button class="btn">Add transaction</button>
</form>
</template>

<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';
import { defineEmits } from 'vue';

    const text = ref('');
    const amount = ref('');
    const emit = defineEmits(['transactionsSubmitted'])

    const toast = useToast()

    const onSubmit = function () {
        if(!text.value || !amount.value) {
            toast.error('Both fields must be filled');
            return;
        }
        const transActionsData = {
            text: text.value,
            amount: parseFloat(amount.value)
        }
        emit('transactionsSubmitted', transActionsData);
        text.value = '',
        amount.value = ''
    }
</script>

<style lang="scss" scoped>

</style>
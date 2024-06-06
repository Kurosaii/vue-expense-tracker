<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const toast = useToast();

const emit = defineEmits(['transactionSubmitted']);

const amount = ref('');
const title = ref('');

function onSubmit() {
    if (!title.value || !amount.value) {
        toast.error('Both fields must be filled');
    } else {
        const transactionData = {
            title: title.value,
            amount: parseFloat(amount.value),
        };

        emit('transactionSubmitted', transactionData);
    }

    title.value = '';
    amount.value = '';
}
</script>

<template>
    <h3>Add New Transaction</h3>

    <form
        id="form"
        @submit.prevent="onSubmit"
    >
        <div class="form-control">
            <label for="title">Title<sup>*</sup></label>
            <input
                id="title"
                v-model="title"
                type="text"
                placeholder="Enter title..."
            />
        </div>

        <div class="form-control">
            <label for="amount">
                Amount<sup>*</sup><br />
                (negative - expense, positive - income)
            </label>
            <input
                id="amount"
                v-model="amount"
                type="number"
                placeholder="Enter amount..."
            />
        </div>

        <button class="btn">Add Transaction</button>
    </form>
</template>

<style scoped>
sup {
    color: red;
}
</style>
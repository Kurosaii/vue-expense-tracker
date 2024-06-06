<script setup>
const emit = defineEmits(['transactionDeleted']);

const props = defineProps({
    transactions: {
        type: Array,
        required: true,
    },
});

function deleteTransaction(id) {
    emit('transactionDeleted', id);
}
</script>

<template>
    <h3>History</h3>

    <ul
        id="list"
        class="list"
        v-if="transactions.length"
    >
        <li
            v-for="transaction in props.transactions"
            :key=transaction.id
            :class="transaction.amount < 0 ? 'minus' : 'plus'"
        >
            <button
                class=" delete-btn"
                @click="deleteTransaction(transaction.id)"
            >x</button>
            {{ transaction.title }}<span>${{ transaction.amount }}</span>
        </li>
    </ul>
    <div v-else>No transactions</div>
</template>

<style scoped>
div {
    color: gray;
}
</style>
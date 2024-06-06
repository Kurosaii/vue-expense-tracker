<script setup>
const props = defineProps({
    transactions: {
        type: Array,
        required: true,
    },
});
</script>

<template>
    <h3>History</h3>

    <ul
        id="list"
        class="list"
    >
        <li
            v-for="transaction in props.transactions"
            :key=transaction.id
            :class="transaction.amount < 0 ? 'minus' : 'plus'"
        >
            <button class=" delete-btn">x</button>
            {{ transaction.title }}<span>${{ transaction.amount }}</span>
        </li>
    </ul>
</template>
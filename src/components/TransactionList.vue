<script setup>
const transactions = [
    {
        id: 1,
        title: 'Flower',
        amount: -19.99,
    },
    {
        id: 2,
        title: 'Salary',
        amount: 299.97,
    },
    {
        id: 3,
        title: 'Book',
        amount: -10,
    },
    {
        id: 4,
        title: 'Camera',
        amount: 150,
    },
];
</script>

<template>
    <h3>History</h3>

    <ul
        id="list"
        class="list"
    >
        <li
            v-for="transaction in transactions"
            :key=transaction.id
            :class="transaction.amount < 0 ? 'minus' : 'plus'"
        >
            <button class=" delete-btn">x</button>
            {{ transaction.title }}<span>${{ transaction.amount }}</span>
        </li>
    </ul>
</template>
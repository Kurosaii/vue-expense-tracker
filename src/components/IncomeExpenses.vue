<script setup>
const props = defineProps({
    expenses: {
        type: String,
        required: true,
    },

    income: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <div class="inc-exp-container">
        <div>
            <h4>Income</h4>
            <p
                id="money-plus"
                class="money plus"
            >${{ props.income }}</p>
        </div>

        <div>
            <h4>Expense</h4>
            <p
                id="money-minus"
                class="money minus"
            >${{ props.expenses }}</p>
        </div>
    </div>
</template>
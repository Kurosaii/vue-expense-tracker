<script setup>
const props = defineProps({
    total: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <h4>Your Balance</h4>

    <h1 id="balance">${{ props.total }}</h1>
</template>
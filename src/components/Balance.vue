<template>
    <h4 class="tracking-wide mt-6">Your Balance</h4>
    <h2 id="balance" class="font-semibold text-2xl">${{ total.toFixed(2) }}</h2>
</template>

<script lang="ts" setup>
    const props = defineProps({
        total: {
            type: Number,
            required: true,
        }
    })
</script>
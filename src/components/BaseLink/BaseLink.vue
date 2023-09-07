<script setup>
defineProps({
    to: {
        type: String,
        required: false,
        default: '/'
    }
});
</script>

<template>
    <a :href="to"><slot /></a>
</template>

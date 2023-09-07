<script setup>
defineProps({
    label: {
        type: String,
        required: false,
        default: ''
    }
});
</script>

<template>
    <label :class="$style.label"><input v-bind="$attrs" :class="$style.input" type="checkbox" />{{ label }}</label>
</template>

<style module>
.label {
    flex-grow: 1;

    display: flex;
    align-items: center;

    gap: 12px;

    color: var(--color-text-primary);
}

.input {
    appearance: none;

    width: 20px;
    height: 20px;
    border: 1px solid var(--color-border);

    text-align: center;

    border-radius: 3px;
    background-color: var(--color-white);
}

.input:hover,
.input:focus {
    border-color: var(--color-accent);
}

.input:checked {
    background-color: var(--color-accent);
    border-color: var(--color-accent);
}

.input:checked::before {
    content: url('@/assets/check-icon.svg');
}
</style>

<script setup>
defineProps({
    variant: {
        type: String,
        required: false,
        default: 'flat'
    }
});
</script>

<template>
    <button
        :class="{
            [$style.button]: true,
            [$style['button_outline']]: variant === 'outline',
            [$style['button_flat']]: variant === 'flat',
            [$style['button_text']]: variant === 'text',
            [$style['button_off']]: variant === 'off'
        }"
    >
        <slot />
    </button>
</template>

<style module>
.button {
    min-width: 70px;
    min-height: 38px;
    width: 70px;
    height: 38px;

    border: 1px solid var(--color-accent);

    border-radius: 8px;
    font-size: 14px;
    font-weight: 700;

    cursor: pointer;
}

.button_outline {
    background-color: var(--color-white);
    color: var(--color-accent);
}

.button_outline:hover {
    background-color: var(--color-accent);
    color: var(--color-white) !important;
}

.button_flat {
    background-color: var(--color-accent);
    color: var(--color-white);
}

.button_text {
    background-color: transparent;
    color: var(--color-text-secondary);
    border-color: transparent;
    text-decoration: underline;
}

.button_text:active {
    color: var(--color-text-primary);
}

.button_off {
    background-color: var(--color-white);
    color: var(--color-text-secondary);
    border-color: var(--color-border);
}
</style>

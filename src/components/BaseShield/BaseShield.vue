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
    <div
        :class="{
            [$style.shield]: true,
            [$style['shield_outline']]: variant === 'outline',
            [$style['shield_flat']]: variant === 'flat'
        }"
    >
        <slot name="prepend" />
        <span><slot /></span>
        <slot name="append" />
    </div>
</template>

<style module>
.shield {
    display: inline-flex;

    width: min-content;

    padding: 8px 10px;

    align-items: center;
    justify-content: center;

    gap: 4px;

    border: 1px solid var(--color-accent);

    border-radius: 4px;
    font-size: 14px;
    font-weight: 700;

    text-wrap: nowrap;
}

.shield_outline {
    background-color: var(--color-white);
    color: var(--color-text-primary);
    border-color: var(--color-border);
}

.shield_flat {
    background-color: var(--color-accent);
    color: var(--color-white);
}

.shield_outline > span {
    color: inherit;
}

.shield_flat > span {
    color: inherit;
}
</style>

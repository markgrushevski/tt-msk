<script setup></script>

<template>
    <div :class="$style.wrapper">
        <span>Цена</span>
        <div :class="$style.slider">
            <div>от<input type="number" />₽</div>
            <div>&nbsp;—&nbsp;</div>
            <div>до<input type="number" />₽</div>
        </div>
    </div>
</template>

<style module>
.wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;

    gap: 16px;
}

.slider {
    display: flex;
    align-items: center;
    justify-content: space-between;

    max-width: 100%;

    gap: 16px;

    color: var(--color-text-secondary);
}

.slider > *:first-child,
.slider > *:last-child {
    display: flex;
    align-items: center;

    padding: 10px 8px;

    gap: 6px;

    border: 1px solid var(--color-border);

    border-radius: 4px;
}

.slider > *:first-child > input,
.slider > *:last-child > input {
    width: 100%;

    color: var(--color-text-primary);
}
</style>

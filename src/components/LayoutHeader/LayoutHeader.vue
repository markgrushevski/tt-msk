<script setup></script>

<template>
    <header :class="$style.header">
        <div style="display: flex; align-items: center; justify-content: space-between; gap: 24px">
            <slot name="prepend"></slot>
        </div>

        <slot />

        <div style="display: flex; align-items: center; justify-content: space-between; text-align: center; gap: 24px">
            <slot name="append"></slot>
        </div>
    </header>
</template>

<style module>
.header {
    flex-shrink: 0;

    display: flex;
    justify-content: center;
    align-items: center;

    padding: 12px 0;

    gap: 24px;
}

@media (width <= 960px) {
    .header {
        display: grid;

        grid-template-rows: auto auto auto;
    }
}
</style>

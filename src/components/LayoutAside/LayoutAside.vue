<script setup></script>

<template>
    <aside :class="$style.aside"><slot /></aside>
</template>

<style module>
.aside {
    flex-shrink: 0;

    display: flex;
    flex-direction: column;

    width: 280px;
}

.aside > *:not(:first-child) {
    padding-top: 28px;
}

@media (width <= 960px) {
    .aside {
        display: none;
    }
}
</style>

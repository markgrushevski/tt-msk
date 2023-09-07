<script setup></script>

<template>
    <span :class="IconWrapper.wrapper"><slot /></span>
</template>

<style module="IconWrapper">
.wrapper {
    display: inline-block;
    min-width: 24px;
    min-height: 24px;
    width: 24px;
    height: 24px;
}

.wrapper svg {
    width: 100%;
    height: 100%;
    fill: var(--color-icons);
}
</style>

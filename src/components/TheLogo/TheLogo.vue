<script setup>
import { LogoIcon } from '@/icons';
</script>

<template>
    <div :class="$style.logo"><LogoIcon />Логотип</div>
</template>

<style module>
.logo {
    display: inline-flex;

    height: 48px;

    padding: 0 24px;

    justify-content: center;
    align-items: center;

    gap: 8px;
}
</style>

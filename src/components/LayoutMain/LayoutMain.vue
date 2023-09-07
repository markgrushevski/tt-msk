<script setup></script>

<template>
    <div :class="$style.main">
        <slot name="prepend" />

        <main>
            <slot />
        </main>
    </div>
</template>

<style module>
.main {
    display: flex;
    align-items: flex-start;

    gap: 36px;
}

.main > main {
    display: grid;
    grid-template-columns: auto auto auto auto;
    margin: 0 auto;
    justify-content: center;
    align-items: center;

    gap: 24px;
}

@media (width <= 960px) {
    .main > main {
        grid-template-columns: auto auto;
        column-gap: 12px;
        row-gap: 16px;
    }
}
</style>

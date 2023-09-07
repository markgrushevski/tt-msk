<script setup>
import { SearchBar, BaseButton, BaseCheckbox } from '@/components';

defineProps({
    filterName: {
        type: String,
        required: true
    },
    attributeList: {
        type: Array,
        required: true
    },
    withSearch: {
        type: Boolean,
        required: true
    }
});
</script>

<template>
    <div :class="$style.wrapper">
        <div :class="$style.header" :style="withSearch ? '' : 'justify-content: center'">
            <span>{{ filterName }}</span>
            <BaseButton v-if="withSearch" variant="text">Очистить</BaseButton>
        </div>
        <SearchBar v-if="withSearch" style="height: 38px; flex-grow: 0" placeholder="Поиск" />
        <div :class="$style.list">
            <div v-for="attribute in attributeList" :key="attribute.id">
                <BaseCheckbox :label="attribute.value" />
                <span>{{ attribute.count }}</span>
            </div>
        </div>
    </div>
</template>

<style module>
.wrapper {
    display: flex;
    flex-direction: column;

    gap: 16px;
}

.header {
    display: flex;
    justify-content: space-between;

    text-align: center;
    font-weight: 700;
}

.list {
    display: flex;
    flex-direction: column;

    overflow-y: auto;
    max-height: 65%;

    gap: 12px;

    color: var(--color-text-secondary);
}

.list > * {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-right: 16px;
}
</style>

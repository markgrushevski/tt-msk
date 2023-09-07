<script setup>
import { ArrowDownIcon } from '@/icons';
import { ref } from 'vue';
import { CategoryFilter } from '@/components';

defineProps({
    name: {
        type: String,
        required: true
    },
    count: {
        type: Number,
        required: true
    },
    categoryList: {
        type: Array,
        required: true
    }
});

const showDropdown = ref(false);
</script>

<template>
    <div :class="$style.category">
        <div :class="$style.button" @click="showDropdown = !showDropdown">
            <span :class="$style.name">
                <ArrowDownIcon
                    :style="categoryList.length ? '' : 'visibility: hidden'"
                    :direction="showDropdown ? '' : 'right'"
                />
                {{ name }}
            </span>
            <span>{{ count }}</span>
        </div>

        <template v-if="categoryList.length">
            <CategoryFilter
                v-for="category in categoryList"
                v-show="showDropdown"
                :key="category.id"
                :category-list="category.categoryList"
                :count="category.count"
                :name="category.name"
            />
        </template>
    </div>
</template>

<style module>
.category {
    display: flex;
    flex-direction: column;

    overflow-y: auto;

    cursor: pointer;
}

.category > .category {
    padding-left: 8px;
}

.button {
    display: flex;

    padding-right: 16px;

    align-items: center;
    justify-content: space-between;

    border-radius: 5px;
}

.button:active {
    background-color: var(--color-bg-tertiary);
}

.button > span {
    color: var(--color-text-secondary);
}

.button:hover > span:first-of-type {
    color: var(--color-text-hover);
}

.name {
    display: inline-flex;
    align-items: center;

    padding: 8px 0;

    color: var(--color-text-primary);
}
</style>

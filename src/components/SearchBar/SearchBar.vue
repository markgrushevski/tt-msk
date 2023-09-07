<script setup>
import { SearchIcon, ClearIcon } from '@/icons';
import { computed, ref } from 'vue';

const props = defineProps({
    modelValue: {
        type: String,
        required: false,
        default: null
    },
    placeholder: {
        type: String,
        required: false,
        default: ''
    }
});

const emit = defineEmits(['update:modelValue']);

const _model = ref('');

const model = computed({
    get() {
        return props.modelValue ?? _model.value;
    },
    /** @param {string} value */
    set(value) {
        emit('update:modelValue', value);
        _model.value = value;
    }
});
</script>

<template>
    <div :class="$style['search-bar']">
        <slot name="prepend" />
        <SearchIcon />
        <input v-model="model" :placeholder="placeholder" type="search" />
        <ClearIcon :class="{ [$style['hidden-icon']]: !model.length }" @click="model = ''" />
        <slot name="append" />
    </div>
</template>

<style module>
.search-bar {
    flex-grow: 1;

    display: flex;

    height: 48px;

    padding-right: 4px;
    padding-left: 16px;

    justify-content: space-between;
    align-items: center;

    gap: 8px;

    border: 1px solid var(--color-border);

    border-radius: 10px;
    background-color: #ffffff;
}

.search-bar:hover,
.search-bar:focus,
.search-bar:focus-visible,
.search-bar:focus-within {
    border-color: var(--color-accent);
}

.search-bar > input {
    width: 100%;
    height: 100%;
}

.search-bar > input::-webkit-search-cancel-button {
    display: none;
}

.search-bar > input::-ms-clear {
    display: none;
}

.hidden-icon {
    visibility: hidden;
}
</style>

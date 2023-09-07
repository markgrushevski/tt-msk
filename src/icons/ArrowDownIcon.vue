<script setup>
import { computed } from 'vue';
import IconWrapper from './IconWrapper.vue';
const p = defineProps({
    direction: {
        type: String,
        required: false,
        default: 'down'
    }
});

const angle = computed(() => {
    switch (p.direction) {
        case 'right':
            return '270';
        case 'up':
            return '180';
        case 'left':
            return '90';
        default:
            return '0';
    }
});
</script>

<template>
    <IconWrapper>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <path
                :transform="`rotate(${angle} 12 12)`"
                d="M7.41,8.58L12,13.17L16.59,8.58L18,10L12,16L6,10L7.41,8.58Z"
            />
        </svg>
    </IconWrapper>
</template>

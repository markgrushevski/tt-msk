<script setup>
import { HotIcon } from '@/icons';
import { BaseButton, BaseShield } from '@/components';

defineProps({
    brand: {
        type: String,
        required: true
    },
    productName: {
        type: String,
        required: true
    },
    brandLink: {
        type: String,
        required: true
    },
    productLink: {
        type: String,
        required: true
    },
    price: {
        type: Number,
        required: true
    },
    oldPrice: {
        type: [Number, null],
        required: true
    },
    currency: {
        type: String,
        required: true
    },
    isHot: {
        type: Boolean,
        required: true
    },
    isOutOfStock: {
        type: Boolean,
        required: true
    }
});
</script>

<template>
    <div :class="$style.card">
        <a
            :class="{
                [$style['image-wrapper']]: true,
                [$style['image-wrapper_out']]: isOutOfStock
            }"
            :href="brandLink"
        >
            <img src="@/assets/product-icon.svg" alt="" />

            <BaseShield v-if="isHot" :class="$style['hot-icon']" variant="outline">
                Хит продаж
                <template #append><HotIcon /></template>
            </BaseShield>

            <BaseShield v-if="oldPrice" :class="$style['sale-icon']">
                {{ 100 - Math.floor((price / oldPrice) * 100) }}%
            </BaseShield>
        </a>

        <a :class="$style.brand" :href="brandLink">{{ brand }}</a>

        <a :class="$style['product-name']" :href="productLink">{{ productName }}</a>

        <div v-if="!isOutOfStock" :class="$style.price">
            <span>{{ price + currency }}</span>
            <span v-if="oldPrice">{{ oldPrice + currency }}</span>
        </div>

        <BaseButton v-if="isOutOfStock" variant="off" style="width: 100%">Сообщить о поступлении</BaseButton>
        <BaseButton v-else variant="outline">Купить</BaseButton>
    </div>
</template>

<style module>
.card {
    display: flex;
    flex-direction: column;

    min-width: 165px;
    max-width: 330px;
    width: 100%;
    height: 360px;

    gap: 16px;

    border-radius: 4px;
}

.image-wrapper {
    position: relative;

    display: block;
    height: 200px;

    background-color: var(--color-bg-primary);
}

.image-wrapper_out {
    background-color: var(--color-bg-secondary);
}

.hot-icon {
    position: absolute;

    top: 5%;
    left: 5%;
}

.sale-icon {
    position: absolute;

    left: 5%;
    bottom: 5%;
}

.brand {
    font-size: 14px;
    color: var(--color-text-secondary);
}

.product-name {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;

    font-size: 14px;
    color: var(--color-text-primary);
}

.card:hover .product-name,
.card:focus .product-name,
.card:focus-within .product-name,
.card:focus-visible .product-name,
.card:active .product-name {
    color: var(--color-text-hover);
}

.price {
    display: flex;
    align-items: center;

    gap: 8px;

    font-weight: 700;
}

.price > span:nth-of-type(2) {
    font-size: 12px;
    color: var(--color-text-secondary);
    text-decoration-line: line-through;
}
</style>

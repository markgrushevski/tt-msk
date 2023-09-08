<script setup>
import {
    BaseButton,
    BaseLink,
    CategoryFilter,
    LayoutAside,
    LayoutHeader,
    LayoutMain,
    ProductCard,
    SearchBar,
    TheLogo,
    CheckboxFilter,
    SliderFilter
} from '@/components';

import { categoriesExample, checkboxesExample, productsExample } from './data.js';
</script>

<template>
    <LayoutHeader>
        <template #prepend>
            <TheLogo />
            <BaseButton style="height: 48px; width: 104px; color: inherit" variant="outline"> Каталог </BaseButton>
        </template>

        <SearchBar placeholder="Поиск по 100 000 товаров">
            <template #append><BaseButton>Найти</BaseButton></template>
        </SearchBar>

        <template #append>
            <BaseLink>Информация о компании</BaseLink>
            <BaseLink>Контакты</BaseLink>
            <BaseLink>Полезные ссылки</BaseLink>
        </template>
    </LayoutHeader>

    <LayoutMain>
        <template #prepend>
            <LayoutAside>
                <div>
                    <CategoryFilter v-for="category in categoriesExample" :key="category.id" v-bind="category" />
                </div>
                <SliderFilter />
                <CheckboxFilter v-for="filter in checkboxesExample" :key="filter.id" v-bind="filter" />
            </LayoutAside>
        </template>

        <ProductCard v-for="product in productsExample" :key="product.id" v-bind="product" />
    </LayoutMain>
</template>

<style>
#app {
    display: flex;
    flex-direction: column;

    gap: 24px;

    padding: 0 100px 36px;
}

@media (width <= 960px) {
    #app {
        padding: 0 16px;
    }
}
</style>

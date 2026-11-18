<template>
    <div class="page">
        <h1>Товары</h1>
        <div class="filters">
            <button :class="{ active: filter === 'all' }" @click="setFilter('all')">
                Все
            </button>
            <button :class="{ active: filter === 'electronics' }" @click="setFilter('electronics')">
                Электроника
            </button>
        <button :class="{ active: filter === 'clothing' }" @click="setFilter('clothing')">
            Одежда
        </button>
        </div>
        <ul class="product-list">
        <li 
            v-for="product in filteredProducts" :key="product.id" 
            class="product-item">
            <RouterLink 
                :to="{ name: 'ProductDetail', params: { id: product.id } }" class="product-link">
                <strong>{{ product.name }}</strong> - {{ product.category }} {{ product.price }} ₽
            </RouterLink>
        </li>
        </ul>
        <p v-if="filteredProducts.length === 0">Нет товаров по выбранному фильтру.</p>
    </div>
</template>
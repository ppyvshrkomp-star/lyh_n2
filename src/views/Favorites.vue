<template>
  <div class="favorites-page">
    <h1 class="page-title">Favorites</h1>

    <div class="products-grid">
      <ProductCard
        v-for="product in products"
        :key="product.id"
        :name="product.name"
        :price="product.price"
        :rating="product.rating"
        :reviews="product.reviews"
        :image="product.image"
        :liked="product.liked"
      />
    </div>
  </div>
</template>

<script setup>
import ProductCard from '../components/ProductCard.vue'
import { products } from '../data/products.js'
</script>

<style scoped>
.favorites-page {
  font-family: 'Nunito', sans-serif;
}

.page-title {
  font-size: 22px;
  font-weight: 800;
  color: #1f2937;
  margin: 0 0 24px 0;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

@media (max-width: 1100px) {
  .products-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .products-grid {
    grid-template-columns: 1fr;
  }
}
</style>
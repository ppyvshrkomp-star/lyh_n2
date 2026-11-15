<template>
  <div class="products-page">
    <!-- Banner -->
    <div class="promo-banner">
      <button class="banner-nav prev">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="20" height="20">
          <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
        </svg>
      </button>

      <div class="banner-content">
        <span class="banner-date">September 12-22</span>
        <h1 class="banner-title">Enjoy free home delivery in this summer</h1>
        <p class="banner-desc">Designer Dresses - Pick from trendy Designer Dress.</p>
        <button class="banner-cta">Get Started</button>
      </div>

      <button class="banner-nav next">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="20" height="20">
          <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7" />
        </svg>
      </button>
    </div>

    <!-- Ürün Grid -->
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
.products-page {
  font-family: 'Nunito', sans-serif;
}

.promo-banner {
  position: relative;
  background: linear-gradient(135deg, #7C3AED 0%, #8B5CF6 50%, #A78BFA 100%);
  border-radius: 14px;
  padding: 48px 64px;
  color: #ffffff;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 28px;
  overflow: hidden;
}

.promo-banner::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -10%;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
  border-radius: 50%;
}

.banner-nav {
  background: rgba(255, 255, 255, 0.2);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: #ffffff;
  transition: background 0.2s;
  flex-shrink: 0;
  z-index: 1;
}

.banner-nav:hover {
  background: rgba(255, 255, 255, 0.3);
}

.banner-content {
  flex: 1;
  z-index: 1;
}

.banner-date {
  display: inline-block;
  font-size: 13px;
  font-weight: 500;
  opacity: 0.9;
  margin-bottom: 8px;
}

.banner-title {
  font-size: 28px;
  font-weight: 800;
  margin: 0 0 8px 0;
  line-height: 1.2;
  max-width: 500px;
}

.banner-desc {
  font-size: 14px;
  opacity: 0.9;
  margin: 0 0 20px 0;
}

.banner-cta {
  background: #f97316;
  color: #ffffff;
  border: none;
  padding: 10px 24px;
  border-radius: 8px;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s;
}

.banner-cta:hover {
  background: #ea580c;
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

  .promo-banner {
    padding: 32px 24px;
  }

  .banner-title {
    font-size: 22px;
  }
}
</style>
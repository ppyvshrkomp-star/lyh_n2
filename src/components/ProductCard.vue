<template>
  <div class="product-card">
    <div class="product-image-wrapper">
      <div class="product-placeholder">
        <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" fill="none" viewBox="0 0 24 24" stroke="#9ca3af" stroke-width="1.5">
          <path stroke-linecap="round" stroke-linejoin="round" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
      </div>
      <button class="like-btn" :class="{ liked: isLiked }" @click="toggleLike">
        <svg v-if="isLiked" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="#ef4444" width="18" height="18">
          <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="#9ca3af" stroke-width="2" width="18" height="18">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
        </svg>
      </button>
    </div>

    <div class="product-info">
      <h3 class="product-name">{{ name }}</h3>
      <div class="product-price">{{ price }}</div>

      <div class="product-rating">
        <div class="stars">
          <svg v-for="i in 5" :key="i" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="14" height="14"
               :fill="i <= rating ? '#fbbf24' : '#e5e7eb'">
            <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
          </svg>
        </div>
        <span class="review-count">({{ reviews }})</span>
      </div>

      <button class="edit-btn">Edit Product</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  name: { type: String, required: true },
  price: { type: String, required: true },
  rating: { type: Number, required: true },
  reviews: { type: Number, required: true },
  image: { type: String, default: null },
  liked: { type: Boolean, default: false },
})

const isLiked = ref(props.liked)

const toggleLike = () => {
  isLiked.value = !isLiked.value
}
</script>

<style scoped>
.product-card {
  background: #ffffff;
  border-radius: 12px;
  padding: 16px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  border: 1px solid #f0f0f0;
  font-family: 'Nunito', sans-serif;
  display: flex;
  flex-direction: column;
}

.product-image-wrapper {
  position: relative;
  width: 100%;
  height: 180px;
  background: #f9fafb;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 14px;
}

.product-placeholder {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: linear-gradient(135deg, #d1d5db 0%, #9ca3af 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.like-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: #ffffff;
  border: none;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
  transition: transform 0.2s;
}

.like-btn:hover {
  transform: scale(1.1);
}

.like-btn.liked svg {
  fill: #ef4444;
}

.product-info {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.product-name {
  font-size: 14px;
  font-weight: 600;
  color: #1f2937;
  margin: 0;
}

.product-price {
  font-size: 14px;
  font-weight: 700;
  color: #7C3AED;
}

.product-rating {
  display: flex;
  align-items: center;
  gap: 6px;
}

.stars {
  display: flex;
  gap: 2px;
}

.review-count {
  font-size: 12px;
  color: #9ca3af;
}

.edit-btn {
  margin-top: 8px;
  padding: 8px 16px;
  background: #F4F2FF;
  color: #7C3AED;
  border: none;
  border-radius: 8px;
  font-family: 'Nunito', sans-serif;
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  align-self: flex-start;
}

.edit-btn:hover {
  background: #EDE9FE;
}
</style>
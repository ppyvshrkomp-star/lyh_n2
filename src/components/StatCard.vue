<template>
  <div class="stat-card">
    <div class="stat-header">
      <div class="stat-title">{{ title }}</div>
      <div class="stat-icon" :style="{ background: iconBg }">
        <span class="icon-emoji">{{ icon }}</span>
      </div>
    </div>
    <div class="stat-value">{{ value }}</div>
    <div class="stat-trend" :class="trend">
      <svg v-if="trend === 'up'" class="trend-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
        <path stroke-linecap="round" stroke-linejoin="round" d="M7 11l5-5m0 0l5 5m-5-5v12" />
      </svg>
      <svg v-else class="trend-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
        <path stroke-linecap="round" stroke-linejoin="round" d="M17 13l-5 5m0 0l-5-5m5 5V6" />
      </svg>
      <span class="trend-text">{{ change }}</span>
      <span class="trend-label">{{ trendLabel }}</span>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: { type: String, required: true },
  value: { type: [String, Number], required: true },
  icon: { type: String, required: true },
  iconBg: { type: String, required: true },
  change: { type: String, required: true },
  trend: { type: String, required: true, validator: (v) => ['up', 'down'].includes(v) },
  trendLabel: { type: String, default: '' },
})
</script>

<style scoped>
.stat-card {
  background: #ffffff;
  border-radius: 12px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  border: 1px solid #f0f0f0;
  font-family: 'Nunito', sans-serif;
}

.stat-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.stat-title {
  font-size: 13px;
  font-weight: 500;
  color: #6b7280;
}

.stat-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.icon-emoji {
  font-size: 18px;
}

.stat-value {
  font-size: 26px;
  font-weight: 700;
  color: #1f2937;
  line-height: 1;
}

.stat-trend {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 12px;
  font-weight: 600;
}

.stat-trend.up {
  color: #10b981;
}

.stat-trend.down {
  color: #ef4444;
}

.trend-icon {
  width: 14px;
  height: 14px;
}

.trend-text {
  font-weight: 700;
}

.trend-label {
  font-weight: 500;
  color: #9ca3af;
}
</style>
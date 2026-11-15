<template>
  <div class="chart-card">
    <div class="chart-header">
      <h2 class="chart-title">Sales Details</h2>
      <select class="month-select">
        <option>October</option>
        <option>September</option>
        <option>August</option>
      </select>
    </div>
    <div class="chart-body">
      <svg viewBox="0 0 800 300" class="chart-svg" preserveAspectRatio="none">
        <!-- Y ekseni etiketleri -->
        <text x="30" y="30" class="axis-label">100%</text>
        <text x="30" y="90" class="axis-label">80%</text>
        <text x="30" y="150" class="axis-label">60%</text>
        <text x="30" y="210" class="axis-label">40%</text>
        <text x="30" y="270" class="axis-label">20%</text>

        <!-- X ekseni etiketleri -->
        <text v-for="(label, i) in xLabels" :key="i" :x="60 + i * 65" y="295" class="axis-label-x">{{ label }}</text>

        <!-- Dolgu alanı -->
        <path :d="fillPath" class="chart-fill" />

        <!-- Çizgi -->
        <path :d="linePath" class="chart-line" />

        <!-- Noktalar -->
        <circle
          v-for="(point, i) in points"
          :key="i"
          :cx="point.x"
          :cy="point.y"
          r="4"
          class="chart-dot"
        />

        <!-- Etiket kutusu (20k noktası) -->
        <g v-if="highlightPoint">
          <rect
            :x="highlightPoint.x - 35"
            :y="highlightPoint.y - 30"
            width="70"
            height="22"
            rx="4"
            class="label-bg"
          />
          <text
            :x="highlightPoint.x"
            :y="highlightPoint.y - 14"
            class="label-text"
          >64,364.77</text>
          <line
            :x1="highlightPoint.x"
            :y1="highlightPoint.y - 8"
            :x2="highlightPoint.x"
            :y2="highlightPoint.y"
            stroke="#7C3AED"
            stroke-width="1"
            stroke-dasharray="3,3"
          />
        </g>
      </svg>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const rawData = [18, 32, 28, 45, 30, 52, 35, 48, 42, 55, 40, 62, 45, 50, 58, 42, 30, 35, 48, 44, 72, 50, 55, 48, 60, 52, 58, 45, 55, 50, 62, 55, 60, 52, 58, 48, 65, 55, 60, 52, 58, 45, 52, 48, 55, 50, 58, 52, 60, 55, 62, 58, 65, 60, 68, 62, 70, 65, 72, 68]

const xLabels = ['5k', '10k', '15k', '20k', '25k', '30k', '35k', '40k', '45k', '50k', '55k', '60k']

const svgWidth = 800
const svgHeight = 300
const paddingX = 60
const paddingY = 20
const chartWidth = svgWidth - paddingX - 20
const chartHeight = svgHeight - paddingY * 2

const points = computed(() => {
  const max = Math.max(...rawData)
  const min = Math.min(...rawData)
  const range = max - min || 1
  return rawData.map((val, i) => ({
    x: paddingX + (i / (rawData.length - 1)) * chartWidth,
    y: paddingY + chartHeight - ((val - min) / range) * chartHeight,
    val,
  }))
})

const linePath = computed(() => {
  return points.value.map((p, i) => `${i === 0 ? 'M' : 'L'} ${p.x} ${p.y}`).join(' ')
})

const fillPath = computed(() => {
  const first = points.value[0]
  const last = points.value[points.value.length - 1]
  return `${linePath.value} L ${last.x} ${svgHeight - paddingY} L ${first.x} ${svgHeight - paddingY} Z`
})

const highlightPoint = computed(() => points.value[20])
</script>

<style scoped>
.chart-card {
  background: #ffffff;
  border-radius: 12px;
  padding: 24px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  border: 1px solid #f0f0f0;
  font-family: 'Nunito', sans-serif;
}

.chart-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}

.chart-title {
  font-size: 18px;
  font-weight: 700;
  color: #1f2937;
  margin: 0;
}

.month-select {
  padding: 6px 12px;
  border: 1px solid #e5e7eb;
  border-radius: 6px;
  font-family: 'Nunito', sans-serif;
  font-size: 13px;
  color: #6b7280;
  background: #ffffff;
  cursor: pointer;
  outline: none;
}

.chart-body {
  width: 100%;
  overflow-x: auto;
}

.chart-svg {
  width: 100%;
  height: 300px;
  display: block;
}

.axis-label {
  font-size: 11px;
  fill: #9ca3af;
  font-family: 'Nunito', sans-serif;
  text-anchor: end;
}

.axis-label-x {
  font-size: 11px;
  fill: #9ca3af;
  font-family: 'Nunito', sans-serif;
  text-anchor: middle;
}

.chart-fill {
  fill: url(#fillGradient);
  opacity: 0.3;
}

.chart-line {
  fill: none;
  stroke: #7C3AED;
  stroke-width: 2;
  stroke-linejoin: round;
  stroke-linecap: round;
}

.chart-dot {
  fill: #7C3AED;
  stroke: #ffffff;
  stroke-width: 2;
}

.label-bg {
  fill: #7C3AED;
}

.label-text {
  fill: #ffffff;
  font-size: 11px;
  font-weight: 600;
  font-family: 'Nunito', sans-serif;
  text-anchor: middle;
}
</style>
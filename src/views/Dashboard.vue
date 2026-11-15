<template>
  <div class="dashboard">
    <div class="stats-grid">
      <StatCard
        title="Total User"
        value="40,689"
        icon="👥"
        iconBg="#EDE9FE"
        change="8.5%"
        trend="up"
        trend-label="Up from yesterday"
      />
      <StatCard
        title="Total Order"
        value="10293"
        icon="📦"
        iconBg="#FEF3C7"
        change="1.3%"
        trend="up"
        trend-label="Up from past week"
      />
      <StatCard
        title="Total Sales"
        value="$89,000"
        icon="📈"
        iconBg="#D1FAE5"
        change="4.3%"
        trend="down"
        trend-label="Down from yesterday"
      />
      <StatCard
        title="Total Pending"
        value="2040"
        icon="⏳"
        iconBg="#FEE2E2"
        change="1.8%"
        trend="up"
        trend-label="Up from yesterday"
      />
    </div>

    <div class="section-gap">
      <SalesChart />
    </div>

    <div class="section-gap">
      <DealsTable />
    </div>
  </div>
</template>

<script setup>
import StatCard from '../components/StatCard.vue'
import SalesChart from '../components/SalesChart.vue'
import DealsTable from '../components/DealsTable.vue'
</script>

<style scoped>
.dashboard {
  font-family: 'Nunito', sans-serif;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

.section-gap {
  margin-top: 24px;
}

@media (max-width: 1200px) {
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .stats-grid {
    grid-template-columns: 1fr;
  }
}
</style>
<template>
  <div class="table-card">
    <div class="table-header">
      <h2 class="table-title">Deals Details</h2>
      <select class="month-select">
        <option>October</option>
        <option>September</option>
        <option>August</option>
      </select>
    </div>
    <div class="table-wrapper">
      <table class="deals-table">
        <thead>
          <tr>
            <th>Product Name</th>
            <th>Location</th>
            <th>Date - Time</th>
            <th>Piece</th>
            <th>Amount</th>
            <th>Status</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="deal in deals" :key="deal.id">
            <td>
              <div class="product-cell">
                <div class="product-avatar" :style="{ background: deal.avatarBg }">
                  {{ deal.name.charAt(0) }}
                </div>
                <span>{{ deal.name }}</span>
              </div>
            </td>
            <td>{{ deal.location }}</td>
            <td>{{ deal.dateTime }}</td>
            <td>{{ deal.piece }}</td>
            <td>{{ deal.amount }}</td>
            <td>
              <span class="status-badge delivered">Delivered</span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
const deals = [
  {
    id: 1,
    name: 'Apple Watch',
    avatarBg: '#FEE2E2',
    location: '6096 Marjolaine Landing',
    dateTime: '12.09.2026 - 12:53 PM',
    piece: 423,
    amount: '$34,295',
  },
  {
    id: 2,
    name: 'MacBook Pro',
    avatarBg: '#DBEAFE',
    location: '1234 Silicon Valley',
    dateTime: '11.09.2026 - 09:15 AM',
    piece: 156,
    amount: '$289,440',
  },
  {
    id: 3,
    name: 'AirPods Pro',
    avatarBg: '#D1FAE5',
    location: '7890 Tech Avenue',
    dateTime: '10.09.2026 - 03:42 PM',
    piece: 892,
    amount: '$22,300',
  },
  {
    id: 4,
    name: 'iPad Air',
    avatarBg: '#FEF3C7',
    location: '456 Innovation Blvd',
    dateTime: '09.09.2026 - 11:20 AM',
    piece: 312,
    amount: '$187,200',
  },
  {
    id: 5,
    name: 'iPhone 16',
    avatarBg: '#EDE9FE',
    location: '221B Baker Street',
    dateTime: '08.09.2026 - 06:08 PM',
    piece: 1024,
    amount: '$1,024,000',
  },
]
</script>

<style scoped>
.table-card {
  background: #ffffff;
  border-radius: 12px;
  padding: 24px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  border: 1px solid #f0f0f0;
  font-family: 'Nunito', sans-serif;
}

.table-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}

.table-title {
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

.table-wrapper {
  overflow-x: auto;
}

.deals-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 14px;
}

.deals-table thead tr {
  background: #F4F2FF;
}

.deals-table th {
  text-align: left;
  padding: 12px 16px;
  font-weight: 600;
  color: #6b7280;
  font-size: 13px;
  white-space: nowrap;
}

.deals-table td {
  padding: 14px 16px;
  color: #374151;
  border-bottom: 1px solid #f3f4f6;
  white-space: nowrap;
}

.deals-table tbody tr:hover {
  background: #fafafa;
}

.product-cell {
  display: flex;
  align-items: center;
  gap: 10px;
}

.product-avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  font-weight: 700;
  color: #7C3AED;
  flex-shrink: 0;
}

.status-badge {
  display: inline-block;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
}

.status-badge.delivered {
  background: #10b981;
  color: #ffffff;
}
</style>
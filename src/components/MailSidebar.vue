<template>
  <aside class="mail-sidebar">
    <button class="compose-btn">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16">
        <path stroke-linecap="round" stroke-linejoin="round" d="M12 4v16m8-8H4" />
      </svg>
      Compose
    </button>

    <div class="sidebar-section">
      <h3 class="section-title">My Email</h3>
      <ul class="folder-list">
        <li v-for="folder in folders" :key="folder.name"
            class="folder-item"
            :class="{ active: folder.name === 'Inbox' }">
          <span class="folder-icon" v-html="folder.icon"></span>
          <span class="folder-name">{{ folder.name }}</span>
          <span class="folder-count">{{ folder.count }}</span>
        </li>
      </ul>
    </div>

    <div class="sidebar-section">
      <h3 class="section-title">Label</h3>
      <ul class="label-list">
        <li v-for="label in labels" :key="label.name" class="label-item">
          <span class="label-color" :style="{ background: label.color }"></span>
          <span class="label-name">{{ label.name }}</span>
        </li>
        <li class="label-item create-label">
          <span class="label-icon">+</span>
          <span class="label-name">Create New Label</span>
        </li>
      </ul>
    </div>
  </aside>
</template>

<script setup>
const folders = [
  { name: 'Inbox', count: '1253', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M20 13V6a2 2 0 00-2-2H6a2 2 0 00-2 2v7m16 0v5a2 2 0 01-2 2H6a2 2 0 01-2-2v-5m16 0h-2.586a1 1 0 00-.707.293l-2.414 2.414a1 1 0 01-.707.293h-3.172a1 1 0 01-.707-.293l-2.414-2.414A1 1 0 006.586 13H4"/></svg>' },
  { name: 'Starred', count: '245', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"/></svg>' },
  { name: 'Sent', count: '24,532', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/></svg>' },
  { name: 'Draft', count: '09', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"/></svg>' },
  { name: 'Spam', count: '14', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>' },
  { name: 'Important', count: '18', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M5 5a2 2 0 012-2h10a2 2 0 012 2v16l-7-3.5L5 21V5z"/></svg>' },
  { name: 'Bin', count: '9', icon: '<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="16" height="16"><path stroke-linecap="round" stroke-linejoin="round" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/></svg>' },
]

const labels = [
  { name: 'Primary', color: '#10b981' },
  { name: 'Social', color: '#3b82f6' },
  { name: 'Work', color: '#f59e0b' },
  { name: 'Friends', color: '#ec4899' },
]
</script>

<style scoped>
.mail-sidebar {
  background: #ffffff;
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  border: 1px solid #f0f0f0;
  font-family: 'Nunito', sans-serif;
  width: 220px;
  flex-shrink: 0;
}

.compose-btn {
  width: 100%;
  background: #7C3AED;
  color: #ffffff;
  border: none;
  padding: 12px;
  border-radius: 10px;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  transition: background 0.2s;
  margin-bottom: 20px;
}

.compose-btn:hover {
  background: #6d28d9;
}

.sidebar-section {
  margin-bottom: 20px;
}

.section-title {
  font-size: 13px;
  font-weight: 700;
  color: #1f2937;
  margin: 0 0 12px 0;
}

.folder-list,
.label-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.folder-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 8px 10px;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.2s;
  font-size: 13px;
  color: #6b7280;
}

.folder-item:hover {
  background: #f9fafb;
}

.folder-item.active {
  background: #EDE9FE;
  color: #7C3AED;
  font-weight: 600;
}

.folder-icon {
  display: flex;
  align-items: center;
  color: inherit;
}

.folder-icon svg {
  stroke: currentColor;
}

.folder-name {
  flex: 1;
}

.folder-count {
  font-size: 12px;
  color: #9ca3af;
}

.folder-item.active .folder-count {
  color: #7C3AED;
}

.label-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 6px 10px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 13px;
  color: #6b7280;
  transition: background 0.2s;
}

.label-item:hover {
  background: #f9fafb;
}

.label-color {
  width: 12px;
  height: 12px;
  border-radius: 3px;
  flex-shrink: 0;
}

.label-name {
  flex: 1;
}

.create-label {
  color: #9ca3af;
  margin-top: 4px;
}

.label-icon {
  font-size: 14px;
  font-weight: 700;
  width: 12px;
  text-align: center;
}
</style>
<template>
  <aside class="sidebar">
    <div class="sidebar-logo">
      <span class="logo-dash">Dash</span><span class="logo-stack">Stack</span>
    </div>

    <nav class="sidebar-nav">
      <ul class="nav-list">
        <li v-for="item in mainMenu" :key="item.path">
          <RouterLink
            :to="item.path"
            class="nav-link"
            :class="{ active: isActive(item.path) }"
            :active-class="''"
          >
            <span class="nav-icon">{{ item.icon }}</span>
            <span class="nav-text">{{ item.label }}</span>
          </RouterLink>
        </li>
      </ul>

      <div class="nav-divider"></div>

      <p class="nav-section-title">Pages</p>

      <ul class="nav-list">
        <li v-for="item in pagesMenu" :key="item.path">
          <RouterLink
            :to="item.path"
            class="nav-link"
            :class="{ active: isActive(item.path) }"
            :active-class="''"
          >
            <span class="nav-icon">{{ item.icon }}</span>
            <span class="nav-text">{{ item.label }}</span>
          </RouterLink>
        </li>
      </ul>

      <div class="nav-divider"></div>

      <ul class="nav-list">
        <li>
          <RouterLink to="/settings" class="nav-link" :class="{ active: isActive('/settings') }">
            <span class="nav-icon">⚙️</span>
            <span class="nav-text">Settings</span>
          </RouterLink>
        </li>
        <li>
          <a href="#" class="nav-link logout-link">
            <span class="nav-icon">🚪</span>
            <span class="nav-text">Logout</span>
          </a>
        </li>
      </ul>
    </nav>
  </aside>
</template>

<script setup>
import { useRoute } from 'vue-router'

const route = useRoute()

const mainMenu = [
  { label: 'Dashboard', path: '/', icon: '📊' },
  { label: 'Products', path: '/products', icon: '📦' },
  { label: 'Favorites', path: '/favorites', icon: '⭐' },
  { label: 'Inbox', path: '/inbox', icon: '📥' },
  { label: 'Order Lists', path: '#', icon: '📋' },
  { label: 'Product Stock', path: '#', icon: '🗃️' },
]

const pagesMenu = [
  { label: 'Pricing', path: '#', icon: '💰' },
  { label: 'Calendar', path: '#', icon: '📅' },
  { label: 'To-Do', path: '#', icon: '✅' },
  { label: 'Contact', path: '#', icon: '📞' },
  { label: 'Invoice', path: '#', icon: '🧾' },
  { label: 'UI Elements', path: '#', icon: '🎨' },
  { label: 'Team', path: '#', icon: '👥' },
  { label: 'Table', path: '#', icon: '🗂️' },
]

const isActive = (path) => {
  if (path === '#') return false
  return route.path === path
}
</script>

<style scoped>
.sidebar {
  width: 240px;
  min-height: 100vh;
  background: #ffffff;
  border-right: 1px solid #e5e7eb;
  padding: 24px 16px;
  display: flex;
  flex-direction: column;
  font-family: 'Nunito', sans-serif;
}

.sidebar-logo {
  font-size: 22px;
  font-weight: 800;
  margin-bottom: 32px;
  padding-left: 12px;
}

.logo-dash {
  color: #7C3AED;
}

.logo-stack {
  color: #1f2937;
}

.sidebar-nav {
  flex: 1;
}

.nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 12px;
  margin-bottom: 4px;
  border-radius: 8px;
  text-decoration: none;
  color: #6b7280;
  font-size: 14px;
  font-weight: 500;
  transition: all 0.2s ease;
}

.nav-link:hover {
  background: #f3f4f6;
  color: #7C3AED;
}

.nav-link.active {
  background: #7C3AED;
  color: #ffffff;
}

.nav-icon {
  font-size: 16px;
  width: 20px;
  text-align: center;
}

.nav-text {
  flex: 1;
}

.nav-divider {
  height: 1px;
  background: #e5e7eb;
  margin: 16px 0;
}

.nav-section-title {
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: #9ca3af;
  padding: 0 12px;
  margin-bottom: 8px;
}

.logout-link {
  color: #ef4444;
}

.logout-link:hover {
  background: #fef2f2;
  color: #ef4444;
}
</style>
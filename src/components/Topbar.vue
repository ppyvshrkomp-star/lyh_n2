<template>
  <header class="topbar">
    <!-- Sol: Logo -->
    <div class="topbar-logo">
      <span class="logo-dash">Dash</span><span class="logo-stack">Stack</span>
    </div>

    <!-- Orta: Arama -->
    <div class="topbar-search">
      <svg class="search-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z" />
      </svg>
      <input type="text" placeholder="Search" class="search-input" />
    </div>

    <!-- Sağ: Aksiyonlar -->
    <div class="topbar-actions">
      <!-- Bildirim -->
      <button class="icon-btn notification-btn">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
        </svg>
        <span class="badge">3</span>
      </button>

      <!-- Dil Seçici -->
      <button class="lang-btn">
        <span class="flag">🇬🇧</span>
        <span class="lang-text">English</span>
        <svg class="chevron" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
        </svg>
      </button>

      <!-- Profil -->
      <div class="profile">
        <div class="profile-avatar">MR</div>
        <div class="profile-info">
          <span class="profile-name">Moni Roy</span>
          <span class="profile-role">Admin</span>
        </div>
        <svg class="chevron-sm" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
        </svg>
      </div>
    </div>
  </header>
</template>

<script setup>
</script>

<style scoped>
.topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #ffffff;
  padding: 12px 24px;
  border-bottom: 1px solid #e5e7eb;
  font-family: 'Nunito', sans-serif;
  gap: 16px;
}

.topbar-logo {
  font-size: 20px;
  font-weight: 800;
  flex-shrink: 0;
}

.logo-dash {
  color: #7C3AED;
}

.logo-stack {
  color: #1f2937;
}

.topbar-search {
  flex: 1;
  max-width: 360px;
  position: relative;
  display: flex;
  align-items: center;
}

.search-icon {
  position: absolute;
  left: 12px;
  width: 18px;
  height: 18px;
  color: #9ca3af;
  pointer-events: none;
}

.search-input {
  width: 100%;
  padding: 10px 14px 10px 40px;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  font-size: 14px;
  font-family: 'Nunito', sans-serif;
  background: #f9fafb;
  color: #374151;
  outline: none;
  transition: border-color 0.2s;
}

.search-input::placeholder {
  color: #9ca3af;
}

.search-input:focus {
  border-color: #7C3AED;
  background: #ffffff;
}

.topbar-actions {
  display: flex;
  align-items: center;
  gap: 8px;
  flex-shrink: 0;
}

.icon-btn {
  position: relative;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s;
}

.icon-btn:hover {
  background: #f3f4f6;
}

.notification-btn svg {
  width: 22px;
  height: 22px;
  color: #7C3AED;
}

.badge {
  position: absolute;
  top: 4px;
  right: 4px;
  background: #ef4444;
  color: #ffffff;
  font-size: 10px;
  font-weight: 700;
  min-width: 16px;
  height: 16px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 4px;
}

.lang-btn {
  display: flex;
  align-items: center;
  gap: 6px;
  background: none;
  border: 1px solid #e5e7eb;
  padding: 6px 12px;
  border-radius: 8px;
  cursor: pointer;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #374151;
  transition: background 0.2s;
}

.lang-btn:hover {
  background: #f9fafb;
}

.flag {
  font-size: 16px;
}

.lang-text {
  color: #374151;
}

.chevron {
  width: 16px;
  height: 16px;
  color: #6b7280;
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 4px 8px 4px 4px;
  border-radius: 10px;
  cursor: pointer;
  transition: background 0.2s;
}

.profile:hover {
  background: #f3f4f6;
}

.profile-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: linear-gradient(135deg, #7C3AED 0%, #a78bfa 100%);
  color: #ffffff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 700;
  flex-shrink: 0;
}

.profile-info {
  display: flex;
  flex-direction: column;
  line-height: 1.2;
}

.profile-name {
  font-size: 14px;
  font-weight: 600;
  color: #1f2937;
}

.profile-role {
  font-size: 12px;
  color: #9ca3af;
}

.chevron-sm {
  width: 16px;
  height: 16px;
  color: #6b7280;
}
</style>
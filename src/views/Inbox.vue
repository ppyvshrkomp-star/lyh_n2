<template>
  <div class="inbox-page">
    <h1 class="page-title">Inbox</h1>

    <div class="inbox-layout">
      <MailSidebar />

      <div class="mail-list-card">
        <!-- Üst bar -->
        <div class="mail-list-header">
          <div class="search-box">
            <svg class="search-icon" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z" />
            </svg>
            <input type="text" placeholder="Search mail" class="search-input" />
          </div>
          <div class="header-actions">
            <button class="icon-btn" title="Archive">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="18" height="18">
                <path stroke-linecap="round" stroke-linejoin="round" d="M5 8h14M5 8a2 2 0 110-4h14a2 2 0 110 4M5 8v10a2 2 0 002 2h10a2 2 0 002-2V8m-9 4h4" />
              </svg>
            </button>
            <button class="icon-btn" title="Delete">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="18" height="18">
                <path stroke-linecap="round" stroke-linejoin="round" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
              </svg>
            </button>
            <button class="icon-btn" title="More">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" width="18" height="18">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 5v.01M12 12v.01M12 19v.01M12 6a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2z" />
              </svg>
            </button>
          </div>
        </div>

        <!-- Mail listesi -->
        <ul class="mail-list">
          <li v-for="mail in emails" :key="mail.id" class="mail-row">
            <input type="checkbox" class="row-checkbox" />
            <button class="star-btn" :class="{ starred: mail.starred }" @click="mail.starred = !mail.starred">
              <svg v-if="mail.starred" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="#fbbf24" width="16" height="16">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
              <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="#d1d5db" stroke-width="2" width="16" height="16">
                <path stroke-linecap="round" stroke-linejoin="round" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"/>
              </svg>
            </button>
            <span class="sender-name">{{ mail.sender }}</span>
            <span v-if="mail.label" class="label-badge" :class="'label-' + mail.label.toLowerCase()">{{ mail.label }}</span>
            <span class="mail-subject">{{ mail.subject }}</span>
            <span class="mail-time">{{ mail.time }}</span>
          </li>
        </ul>

        <!-- Alt bar -->
        <div class="mail-list-footer">
          <span class="showing-text">Showing 1-12 of 1,253</span>
          <div class="pagination-btns">
            <button class="page-btn">&lt;</button>
            <button class="page-btn">&gt;</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import MailSidebar from '../components/MailSidebar.vue'
import { emails } from '../data/emails.js'
</script>

<style scoped>
.inbox-page {
  font-family: 'Nunito', sans-serif;
}

.page-title {
  font-size: 22px;
  font-weight: 800;
  color: #1f2937;
  margin: 0 0 20px 0;
}

.inbox-layout {
  display: flex;
  gap: 20px;
  align-items: flex-start;
}

.mail-list-card {
  flex: 1;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  border: 1px solid #f0f0f0;
  overflow: hidden;
  min-width: 0;
}

.mail-list-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
  border-bottom: 1px solid #f3f4f6;
  gap: 16px;
}

.search-box {
  flex: 1;
  max-width: 360px;
  position: relative;
}

.search-icon {
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
  width: 16px;
  height: 16px;
  color: #9ca3af;
  pointer-events: none;
}

.search-input {
  width: 100%;
  padding: 9px 14px 9px 38px;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  font-family: 'Nunito', sans-serif;
  font-size: 13px;
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

.header-actions {
  display: flex;
  gap: 4px;
}

.icon-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
  border-radius: 6px;
  color: #6b7280;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s;
}

.icon-btn:hover {
  background: #f3f4f6;
}

.mail-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.mail-row {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 20px;
  border-bottom: 1px solid #f3f4f6;
  font-size: 13px;
  transition: background 0.15s;
}

.mail-row:hover {
  background: #fafafa;
}

.row-checkbox {
  width: 16px;
  height: 16px;
  cursor: pointer;
  accent-color: #7C3AED;
  flex-shrink: 0;
}

.star-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  display: flex;
  align-items: center;
  flex-shrink: 0;
}

.star-btn svg {
  transition: transform 0.2s;
}

.star-btn:hover svg {
  transform: scale(1.2);
}

.sender-name {
  font-weight: 600;
  color: #1f2937;
  min-width: 130px;
  flex-shrink: 0;
}

.label-badge {
  padding: 3px 10px;
  border-radius: 12px;
  font-size: 11px;
  font-weight: 600;
  flex-shrink: 0;
}

.label-primary {
  background: #E0E7FF;
  color: #4338CA;
}

.label-work {
  background: #FEF3C7;
  color: #B45309;
}

.label-friends {
  background: #FCE7F3;
  color: #BE185D;
}

.label-social {
  background: #DBEAFE;
  color: #1D4ED8;
}

.mail-subject {
  flex: 1;
  color: #6b7280;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  min-width: 0;
}

.mail-time {
  color: #9ca3af;
  font-size: 12px;
  flex-shrink: 0;
  margin-left: 8px;
}

.mail-list-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 20px;
  border-top: 1px solid #f3f4f6;
}

.showing-text {
  font-size: 13px;
  color: #9ca3af;
}

.pagination-btns {
  display: flex;
  gap: 4px;
}

.page-btn {
  width: 28px;
  height: 28px;
  border: 1px solid #e5e7eb;
  background: #ffffff;
  border-radius: 6px;
  cursor: pointer;
  font-size: 12px;
  color: #6b7280;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s;
}

.page-btn:hover {
  background: #7C3AED;
  color: #ffffff;
  border-color: #7C3AED;
}

@media (max-width: 900px) {
  .inbox-layout {
    flex-direction: column;
  }

  .mail-sidebar {
    width: 100%;
  }
}
</style>
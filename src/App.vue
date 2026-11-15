<template>
  <div class="app-layout">
    <Sidebar />
    <div class="main-wrapper">
      <Topbar />
      <main class="content-area">
        <RouterView />
      </main>
    </div>
  </div>
</template>

<script setup>
import Sidebar from './components/Sidebar.vue'
import Topbar from './components/Topbar.vue'
</script>

<style>
/* Global font ayarı */
body {
  margin: 0;
  padding: 0;
  font-family: 'Nunito', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.app-layout {
  display: flex;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}

.main-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  min-width: 0; /* İçeriğin taşmasını engeller */
}

.content-area {
  flex: 1;
  background-color: #F4F2FF;
  overflow-y: auto;
  padding: 24px;
}
</style>
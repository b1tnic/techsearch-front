<script setup lang="ts">
import { ref } from "vue";
    const sidebarToggleFlag = ref(false)

    const toggleSidebar = () => {
        sidebarToggleFlag.value = !sidebarToggleFlag.value
    }
</script>

<template>
  <img class="sidebar-toggle-icon" @click="toggleSidebar" v-if="!sidebarToggleFlag" src="../../assets/sidebar.svg" alt="サイドバーアイコン">
  <Transition name="sidebar-slide">
    <div  v-if="sidebarToggleFlag" class="sidebar">
      <div class="sidebar-menu">
        <div class="sidebar-menu-logo">
            <img class="sidebar-img" src="../../assets/TECHSEARCH.png" href="/" alt="アイコン">
        </div>
        <router-link to="/about">
            <div class="sidebar-menu-item">
                トップページ
            </div>
        </router-link>
        <router-link to="/">
            <div class="sidebar-menu-item">
                検索
            </div>
        </router-link>
        <router-link to="/terms">
            <div class="sidebar-menu-item">
                ご利用にあたって
            </div>
        </router-link>
      </div>
      <div @click="toggleSidebar" class="sidebar-overlay">
      </div>
    </div>
  </Transition>
</template>

<style scoped>
a {  
    text-decoration: none;
}

.sidebar-img {
    height: 44px;
}

.sidebar-toggle-icon {
    position: absolute;
    top:60px;
    left:40px;
}

.sidebar-toggle-icon:hover {
    opacity:0.7;
}

.sidebar-slide-enter-active,
.sidebar-slide-leave-active {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.sidebar-slide-enter-from .sidebar-menu,
.sidebar-slide-leave-to .sidebar-menu  {
  left: -250px;
}

.sidebar-menu {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 250px;
  background: rgba(20, 25, 40);
  box-shadow: -10px 0 30px rgba(0,0,0,0.15);
  transition: left 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 999;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
}

.sidebar-menu-logo {
    height: 44px;
    padding: 8px 16px;
    margin-bottom:20px;
    text-align:center;
    color: white;
    font-size:20px;
}

.sidebar-menu-item {
    height: 44px;
    padding: 8px 16px;
    text-align:center;
    color: white;
    font-size:20px;
}

.sidebar-menu-item:hover{
    opacity:0.7;
}

.sidebar-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(5px);
  z-index: 998;
  opacity: 0.8;
  transition: opacity 0.4s;
}

.sidebar-slide-enter-from .sidebar-overlay,
.slide-leave-to .sidebar-overlay {
  opacity: 0;
}
</style>
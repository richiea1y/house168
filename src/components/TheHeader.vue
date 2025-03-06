<template>
  <nav class="navbar">
    <div class="logo-container">
      <img src="@/assets/images/Logo.png" alt="house168 logo" />
    </div>
    <div class="nav-links">
      <div
        class="dropdown-nav-item agent-tools"
        @click="toggleAgentTools"
        :class="{ 'dropdown-active': agentToolsDropdownOpen }"
      >
        房仲工具
        <img
          src="@/assets/images/icon/stat-minus_icon.svg"
          alt="toggle-icon"
          :class="{ 'icon-active': agentToolsDropdownOpen }"
        />
        <div v-if="agentToolsDropdownOpen" class="dropdown-menu">
          <div class="dropdown-item">
            <div class="vector-container">
              <img
                src="@/assets/images/icon/dropdown-item_vector1.svg"
                alt="dropdown-item_vector1"
              />
            </div>
            房屋變裝
          </div>
          <div class="dropdown-item">
            <div class="vector-container">
              <img
                src="@/assets/images/icon/dropdown-item_vector2.svg"
                alt="dropdown-item_vector2"
              />
            </div>
            建商製作
          </div>
          <div class="dropdown-item">
            <div class="vector-container">
              <img
                src="@/assets/images/icon/dropdown-item_vector3.svg"
                alt="dropdown-item_vector3"
              />
            </div>
            LINE貼圖
          </div>
          <div class="dropdown-item">
            <div class="vector-container">
              <img
                src="@/assets/images/icon/dropdown-item_vector4.svg"
                alt="dropdown-item_vector4"
              />
            </div>
            銷售報告書
          </div>
          <div class="dropdown-item">
            <div class="vector-container">
              <img
                src="@/assets/images/icon/dropdown-item_vector5.svg"
                alt="dropdown-item_vector5"
              />
            </div>
            顧問型影音
          </div>
          <div class="dropdown-item">
            <div class="vector-container">
              <img
                src="@/assets/images/icon/dropdown-item_vector6.svg"
                alt="dropdown-item_vector6"
              />
            </div>
            浮水印
          </div>
        </div>
      </div>
      <div class="dropdown-nav-item">定價</div>
      <div class="dropdown-nav-item">房屋交易</div>
    </div>
    <div class="user-utility-menu">
      <button class="login-btn">登入</button>
      <button class="membership-btn">
        <img src="@/assets/images/icon/account-circle_icon.svg" alt="account-circle-icon" />會員中心
      </button>
      <div
        class="language-btn"
        @click="toggleLanguageMenu"
        :class="{ 'language-menu-open': languageMenuOpen }"
      >
        <img src="@/assets/images/icon/language_icon.svg" alt="language-icon" />Language
        <div class="language-menu" :class="{ 'language-menu-open': languageMenuOpen }">
          <div class="language-item">繁體中文</div>
          <div class="language-item">日本語</div>
          <div class="language-item">简体中文</div>
          <div class="language-item">Deutsch</div>
          <div class="language-item">English</div>
          <div class="language-item">한국어</div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

// State
const agentToolsDropdownOpen = ref(false);
const languageMenuOpen = ref(false);

// Methods
const toggleAgentTools = () => {
  agentToolsDropdownOpen.value = !agentToolsDropdownOpen.value;
};

const toggleLanguageMenu = () => {
  languageMenuOpen.value = !languageMenuOpen.value;
};

const closeDropdown = event => {
  // Close dropdown when clicking outside
  if (!event.target.closest('.agent-tools')) {
    agentToolsDropdownOpen.value = false;
  }
};

const closeLanguageMenu = event => {
  if (!event.target.closest('.language-btn')) {
    languageMenuOpen.value = false;
  }
};

// Lifecycle hooks
onMounted(() => {
  // Add event listener to close dropdown when clicking outside
  document.addEventListener('click', closeDropdown);
  document.addEventListener('click', closeLanguageMenu);
});

onBeforeUnmount(() => {
  // 清理所有監聽器和響應式數據，避免內存洩漏
  document.removeEventListener('click', closeDropdown);
  agentToolsDropdownOpen.value = false;
  document.removeEventListener('click', closeLanguageMenu);
  languageMenuOpen.value = false;
});
</script>

<style lang="scss">
@use '@/styles/components/_navbar.scss';
</style>

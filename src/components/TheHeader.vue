<template>
  <nav class="navbar">
    <div class="logo-container">
      <img src="@/assets/images/Logo.png" alt="house168 logo" />
    </div>

    <!-- Mobile menu toggle button -->
    <div class="mobile-menu-toggle" @click="toggleMobileMenu">
      <span v-if="!mobileMenuOpen">☰</span>
      <span v-else>✕</span>
    </div>

    <!-- Menu container with both desktop and mobile menus -->
    <div class="menu-container" :class="{ 'mobile-menu-open': mobileMenuOpen }">
      <div class="nav-links" :class="{ 'mobile-visible': mobileMenuOpen }">
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

        <!-- Language dropdown for mobile view -->
        <div
          class="dropdown-nav-item language-dropdown-mobile"
          @click="toggleLanguageMenu"
          :class="{ 'dropdown-active': languageMenuOpen }"
        >
          語言切換
          <img
            src="@/assets/images/icon/stat-minus_icon.svg"
            alt="toggle-icon"
            :class="{ 'icon-active': languageMenuOpen }"
          />
          <div v-if="languageMenuOpen" class="dropdown-menu language-dropdown-menu">
            <div class="dropdown-item language-item-mobile">繁體中文</div>
            <div class="dropdown-item language-item-mobile">日本語</div>
            <div class="dropdown-item language-item-mobile">简体中文</div>
            <div class="dropdown-item language-item-mobile">Deutsch</div>
            <div class="dropdown-item language-item-mobile">English</div>
            <div class="dropdown-item language-item-mobile">한국어</div>
          </div>
        </div>
      </div>

      <!-- User utility menu (login/membership) -->
      <div class="user-utility-menu" :class="{ 'mobile-visible': mobileMenuOpen }">
        <button class="login-btn">會員登入</button>
        <button class="membership-btn">
          <img
            src="@/assets/images/icon/account-circle_icon.svg"
            alt="account-circle-icon"
          />會員中心
        </button>
        <div
          class="language-btn desktop-only"
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
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

// State
const agentToolsDropdownOpen = ref(false);
const languageMenuOpen = ref(false);
const mobileMenuOpen = ref(false);

// Methods
const toggleAgentTools = () => {
  agentToolsDropdownOpen.value = !agentToolsDropdownOpen.value;
};

const toggleLanguageMenu = () => {
  languageMenuOpen.value = !languageMenuOpen.value;
};

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;

  // Close other dropdowns when toggling mobile menu
  if (mobileMenuOpen.value) {
    document.body.style.overflow = 'hidden'; // Prevent scrolling when menu is open
  } else {
    document.body.style.overflow = '';
  }
};

const closeDropdown = event => {
  // Close dropdown when clicking outside
  if (!event.target.closest('.agent-tools')) {
    agentToolsDropdownOpen.value = false;
  }
};

const closeLanguageMenu = event => {
  if (
    !event.target.closest('.language-btn') &&
    !event.target.closest('.language-dropdown-mobile')
  ) {
    languageMenuOpen.value = false;
  }
};

const handleResize = () => {
  // Close mobile menu if screen size increases above mobile threshold
  if (window.innerWidth > 430 && mobileMenuOpen.value) {
    mobileMenuOpen.value = false;
    document.body.style.overflow = '';
  }
};

// Lifecycle hooks
onMounted(() => {
  // Add event listeners
  document.addEventListener('click', closeDropdown);
  document.addEventListener('click', closeLanguageMenu);
  window.addEventListener('resize', handleResize);
});

onBeforeUnmount(() => {
  // Clean up all listeners and reactive data to avoid memory leaks
  document.removeEventListener('click', closeDropdown);
  document.removeEventListener('click', closeLanguageMenu);
  window.removeEventListener('resize', handleResize);

  agentToolsDropdownOpen.value = false;
  languageMenuOpen.value = false;
  mobileMenuOpen.value = false;
  document.body.style.overflow = '';
});
</script>

<style lang="scss">
@use '@/styles/components/_navbar.scss';
</style>

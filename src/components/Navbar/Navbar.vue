<template>
  <nav class="navbar">
    <div class="navbar__logo">
      <img src="@/assets/images/Logo.png" alt="house168 logo" />
    </div>

    <!-- Mobile menu toggle button -->
    <MobileMenu v-model:mobile-menu-status="mobileMenuOpen" v-model:mobile-flag="mobileScreen" />

    <!-- Menu container with both desktop and mobile menus -->
    <div class="navbar__menu" :class="{ 'mobile__menu--open': mobileMenuOpen }">
      <div class="menu__items" :class="{ 'mobile__menu--visible': mobileMenuOpen }">
        <DropdownTools
          label="房仲工具"
          type="tools"
          :items="toolItems"
          v-model:dropdown-status="dropdownToolsOpen"
        />
        <div class="menu__item">定價</div>
        <div class="menu__item">房屋交易</div>
      </div>

      <!-- User utility menu (login/membership) -->
      <div class="user-utility-menu" :class="{ 'mobile__menu--visible': mobileMenuOpen }">
        <button class="login__btn">登入</button>
        <button class="member__btn">
          <img
            class="member__icon"
            src="@/assets/images/icon/member-icon.png"
            alt="account-circle-icon"
          />會員中心
        </button>
        <div
          class="language-btn desktop-only"
          @click="toggleLanguageMenu"
          :class="{ 'language-menu-open': languageMenuOpen }"
        >
          <div v-if="!mobileScreen" class="language-btn-container desktop-only">
            <img src="@/assets/images/icon/language_icon.svg" alt="language-icon" />
            <div class="language-btn-name">Language</div>
          </div>
          <div v-else class="language-btn-container mobile-only">
            <div class="language-btn-name">語言切換</div>
            <img
              src="@/assets/images/icon/stat-minus_icon.svg"
              alt="toggle-icon"
              :class="{ 'icon-active': languageMenuOpen }"
            />
          </div>
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
import DropdownTools from '@/components/Navbar/DropdownTools.vue';
import MobileMenu from '@/components/Navbar/MobileMenu.vue';

// State
const mobileScreen = ref(false);
const mobileMenuOpen = ref(false);

const dropdownToolsOpen = ref(false);
const languageMenuOpen = ref(false);

const toolItems = [
  { id: 1, text: '房屋變裝', iconSrc: '/src/assets/images/icon/tools-icon1.png' },
  { id: 2, text: '建商製作', iconSrc: '/src/assets/images/icon/tools-icon2.png' },
  { id: 3, text: 'LINE貼圖', iconSrc: '/src/assets/images/icon/tools-icon3.png' },
  { id: 4, text: '銷售報告書', iconSrc: '/src/assets/images/icon/tools-icon4.png' },
  { id: 5, text: '顧問型影音', iconSrc: '/src/assets/images/icon/dropdown-item_vector5.svg' },
  { id: 6, text: '浮水印', iconSrc: '/src/assets/images/icon/dropdown-item_vector6.svg' }
];

// const languageItems = ref([
//   { text: '繁體中文' },
//   { text: '日本語' },
//   { text: '简体中文' },
//   { text: 'Deutsch' },
//   { text: 'English' },
//   { text: '한국어' }
// ]);

const toggleLanguageMenu = () => {
  languageMenuOpen.value = !languageMenuOpen.value;
};

// Open mobile flag when viewport width is less than 768px
const handleResize = () => {
  mobileScreen.value = window.innerWidth <= 768;
};

// Lifecycle hooks
onMounted(() => {
  // Initial check
  handleResize();
  // Add event listener
  window.addEventListener('resize', handleResize);
});

onBeforeUnmount(() => {
  // Clean up
  window.removeEventListener('resize', handleResize);
});
</script>

<style lang="scss">
@use '@/styles/layout/_navbar.scss';
</style>

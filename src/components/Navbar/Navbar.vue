<template>
  <section class="header">
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
        <div class="menu__users" :class="{ 'mobile__menu--visible': mobileMenuOpen }">
          <button v-if="!mobileMenuOpen" class="users__login">登入</button>
          <button v-else class="users__login">會員登入</button>
          <button class="users__member">
            <img
              class="member__icon"
              src="@/assets/images/icon/member-icon.png"
              alt="account-circle-icon"
            />
            <div v-if="lgScreenWidth" class="member__label">會員中心</div>
          </button>
        </div>

        <!-- Language menu -->
        <DropdownLanguage
          :class="{ 'mobile__menu--visible': mobileMenuOpen }"
          :language-open="languageMenuOpen"
          :mobile-flag="mobileScreen"
          :lg-screen-width="lgScreenWidth"
          :language-items="languageItems"
          @toggle-language="toggleLanguage"
        />
      </div>
    </nav>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import DropdownTools from '@/components/Navbar/DropdownTools.vue';
import MobileMenu from '@/components/Navbar/MobileMenu.vue';
import DropdownLanguage from '@/components/Navbar/DropdownLanguage.vue';
// State
const mobileScreen = ref(false);
const mobileMenuOpen = ref(false);
const lgScreenWidth = ref(false);

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

const languageItems = ref([
  { id: 1, text: '繁體中文' },
  { id: 2, text: '日本語' },
  { id: 3, text: '简体中文' },
  { id: 4, text: 'Deutsch' },
  { id: 5, text: 'English' },
  { id: 6, text: '한국어' }
]);

const toggleLanguage = () => {
  languageMenuOpen.value = !languageMenuOpen.value;
};

// Open mobile flag when viewport width is less than 768px
const handleResize = () => {
  mobileScreen.value = window.innerWidth <= 768;
};

const handleScreenWidth = () => {
  lgScreenWidth.value = window.innerWidth > 1024;
};

// Lifecycle hooks
onMounted(() => {
  // Initial check
  handleResize();
  // Add event listener
  window.addEventListener('resize', handleResize);
  window.addEventListener('resize', handleScreenWidth);
});

onBeforeUnmount(() => {
  // Clean up
  window.removeEventListener('resize', handleResize);
  window.removeEventListener('resize', handleScreenWidth);
});
</script>

<style lang="scss">
@use '@/styles/layout/navbar';
</style>

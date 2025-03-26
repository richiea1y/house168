<template>
  <div
    class="menu__language desktop-only"
    @click="toggleLanguageMenu"
    :class="{ 'language-menu-open': languageMenuOpen }"
  >
    <div v-if="!mobileScreen" class="language__container desktop-only">
      <img
        class="language__icon"
        src="@/assets/images/icon/language_icon.svg"
        alt="language-icon"
      />
      <div class="language__label">Language</div>
    </div>
    <div v-else class="language__container mobile-only">
      <div class="language__label">語言切換</div>
      <img
        src="@/assets/images/icon/stat-minus_icon.svg"
        alt="toggle-icon"
        class="language__icon"
        :class="{ 'icon-active': languageMenuOpen }"
      />
    </div>
    <div class="language__items" :class="{ 'language-menu-open': languageMenuOpen }">
      <div class="language__item">繁體中文</div>
      <div class="language__item">日本語</div>
      <div class="language__item">简体中文</div>
      <div class="language__item">Deutsch</div>
      <div class="language__item">English</div>
      <div class="language__item">한국어</div>
    </div>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
@use '../../styles/abstract/functions';
@use '../../styles/abstract/variables';
@use '../../styles/components/mobile-menu';

// Language dropdown menu
.menu__language {
  display: flex;
  align-items: center;
  position: relative;
  padding: 0.5em 0.75em;
  cursor: pointer;
  font-size: 16px;
}

.language__container {
  display: flex;
  align-items: center;
  gap: functions.rem(5);
}

.language__icon {
  width: 30px;
  filter: brightness(0);
}

// Language dropdown items
.language__items {
  position: absolute;
  display: none;
  grid-template-columns: repeat(2, 1fr);
  background-color: #fff;
  min-width: 170px;
  padding: 0.5rem 1rem;
  top: 120%;
  left: -75%;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  border-radius: 4px;
  z-index: 100;

  &.language-menu-open {
    display: grid;
  }

  .language__item {
    padding: 0.25rem 0.5rem 0.25rem 0.5rem;
    cursor: pointer;

    &:hover {
      color: variables.$hover-active-color;
    }
  }
}

// Mobile-specific styles for language dropdown
.language-dropdown-mobile {
  display: none;
  img {
    filter: brightness(0);

    &.icon-active {
      filter: brightness(0) sepia(1) hue-rotate(5deg) saturate(5);
    }
  }
  .dropdown-items {
    display: none;

    &.language-dropdown-menu {
      position: absolute;
      top: 100%;
      left: 0;
      background-color: white;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
      min-width: 100%;
      border-top: 2px solid variables.$hover-active-color;
      z-index: 100;
    }
  }
}
</style>

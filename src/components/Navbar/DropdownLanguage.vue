<template>
  <div
    class="menu__language desktop--only"
    @click="$emit('toggleLanguage')"
    :class="{ 'language-menu-open': props.languageOpen }"
  >
    <div v-if="!props.mobileFlag" class="language__container desktop--only">
      <img
        class="language__icon"
        src="@/assets/images/icon/language_icon.svg"
        alt="language-icon"
      />
      <div class="language__label">Language</div>
    </div>
    <div v-else class="language__container mobile--only">
      <div class="language__label mobile-only">語言切換</div>
      <img
        src="@/assets/images/icon/stat-minus_icon.svg"
        alt="toggle-icon"
        class="language__icon mobile--only"
        :class="{ 'icon-active': props.languageOpen }"
      />
    </div>
    <div class="language__items" :class="{ 'language-menu-open': props.languageOpen }">
      <div v-for="item in props.languageItems" :key="item.id" class="language__item">
        {{ item.text }}
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  languageOpen: {
    type: Boolean
  },
  mobileFlag: {
    type: Boolean
  },
  languageItems: {
    type: Array
  }
});

defineEmits(['toggleLanguage']);
</script>

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

  &.mobile--only {
    gap: 0;
  }
}

.language__icon {
  width: 30px;
  filter: brightness(0);

  &.mobile--only {
    max-width: 24px;
  }
}

// Language dropdown items
.language__items {
  display: none;
  background-color: #fff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  border-radius: 4px;
  min-width: 192px;
  padding: 0.5rem 1rem;

  &.language-menu-open {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    position: absolute;
    z-index: 100;
    top: 120%;
    left: -55%;
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

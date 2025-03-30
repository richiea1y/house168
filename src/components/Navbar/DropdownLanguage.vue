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
      <div v-if="props.lgScreenWidth" class="language__label">Language</div>
    </div>
    <div v-else class="language__container mobile__item mobile--only">
      <div class="language__label mobile-only">語言切換</div>
      <img
        src="@/assets/images/icon/stat-minus_icon.svg"
        alt="toggle-icon"
        class="language__icon mobile--only"
        :class="{ 'icon-active': props.languageOpen }"
      />
    </div>
    <!-- Desktop language dropdown items -->
    <div class="language__items mobile__item" :class="{ 'language-menu-open': props.languageOpen }">
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
  },
  lgScreenWidth: {
    type: Boolean
  }
});

defineEmits(['toggleLanguage']);
</script>

<style lang="scss" scoped>
@use '@/styles/abstract/functions';
@use '@/styles/abstract/variables';
@use '@/styles/layout/mobile-menu';

// Language dropdown menu
.menu__language {
  display: flex;
  align-items: center;
  position: relative;
  padding: 0.5em 0.75em;
  cursor: pointer;
  font-size: functions.rem(16);

  @media screen and (max-width: variables.$medium-screen) {
    display: grid;
    grid-template-columns: 1fr;
    justify-content: stretch;
    font-size: functions.rem(18);
    padding: 0;
    margin: 0;
    // margin: 1.6em 0 0 0;
    // border-bottom: 2px solid #d9d9d9;

    .mobile__item {
      border-bottom: 2px solid #d9d9d9;
      padding: 1.6em 2em 0 2em;
    }
  }
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

  @media screen and (max-width: variables.$medium-screen) {
    border-radius: 0;
  }

  &.language-menu-open {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    position: absolute;
    z-index: 100;
    top: 120%;
    left: -55%;

    @media screen and (max-width: variables.$medium-screen) {
      grid-template-columns: 1fr;
      font-size: functions.rem(16);
      padding: {
        top: 0.8em;
        bottom: 0.8em;
        left: 4.1em;
        right: 2em;
      }
      position: relative;
      top: 0;
      left: 0;
      z-index: 0;
      box-shadow: none;
      border-top: none;
    }
  }

  .language__item {
    padding: 0.25rem 0.5rem 0.25rem 0.5rem;
    cursor: pointer;

    &:hover {
      color: variables.$hover-active-color;
    }
  }
}
</style>

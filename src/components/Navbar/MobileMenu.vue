<template>
  <div class="menu__toggle" @click="toggleMobileMenu">
    <span v-if="!mobileMenuStatus" class="menu__toggle--icon">☰</span>
    <span v-else class="menu__toggle--icon">✕</span>
  </div>
</template>

<script setup>
import { watch } from 'vue';

const mobileMenuStatus = defineModel('mobileMenuStatus', {
  type: Boolean,
  default: false
});

const mobileFlag = defineModel('mobileFlag', {
  type: Boolean
});

watch(
  mobileFlag,
  () => {
    console.log(mobileFlag.value);
  },
  { immediate: true }
);

// Methods
const toggleMobileMenu = () => {
  // Close other dropdowns when toggling mobile menu
  mobileMenuStatus.value = !mobileMenuStatus.value;
  // Prevent scrolling when menu is open
  document.body.style.overflow = mobileMenuStatus.value ? 'hidden' : '';
};
</script>

<style lang="scss" scoped>
@use '@/styles/abstract/functions';
@use '@/styles/abstract/variables';

// Mobile menu toggle button
.menu__toggle {
  display: none;
  font-size: functions.rem(24);
  cursor: pointer;
  margin-left: auto;
  z-index: 111;

  &--icon {
    font-size: functions.rem(32);
  }

  // Show mobile menu toggle button on medium screen
  @media screen and (max-width: variables.$medium-screen) {
    display: block;
  }
}
</style>

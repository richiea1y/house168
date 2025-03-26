<template>
  <div
    class="menu__toggle mobile"
    :class="{ 'mobile__toggle--active': mobileMenuStatus }"
    @click="toggleMobileMenu"
  >
    <span v-if="!mobileMenuStatus">☰</span>
    <span v-else>✕</span>
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
@use '../../styles/abstract/functions';
@use '../../styles/components/mobile-menu';

// Mobile menu toggle button
.menu__toggle {
  display: none;
  font-size: functions.rem(24);
  cursor: pointer;
  margin-left: auto;
  z-index: 101;
}
</style>

<template>
  <div class="menu__toggle mobile" @click="toggleMobileMenu">
    <span v-if="!dropdownStatus">☰</span>
    <span v-else>✕</span>
  </div>
</template>

<script setup>
const mobileMenuStatus = defineModel('mobileMenuStatus', {
  type: Boolean,
  default: false
});

// Methods
const toggleMobileMenu = () => {
  mobileMenuStatus.value = !mobileMenuStatus.value;

  // Close other dropdowns when toggling mobile menu
  if (mobileMenuStatus.value) {
    // Prevent scrolling when menu is open
    document.body.style.overflow = 'hidden';
  } else {
    document.body.style.overflow = '';
  }
};
</script>

<style lang="scss" scoped>
@use '../../styles/abstract/functions';
// Mobile menu toggle button
.menu__toggle {
  // display: none;
  font-size: functions.rem(24);
  cursor: pointer;
  margin-left: auto;
  z-index: 101;
}
</style>

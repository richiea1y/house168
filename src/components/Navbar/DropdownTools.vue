<template>
  <div
    class="menu__item dropdown"
    @click="toggleDropdown"
    :class="{ 'dropdown--active': dropdownStatus }"
  >
    <div class="dropdown__label">{{ props.label }}</div>
    <img
      src="@/assets/images/icon/stat-minus_icon.svg"
      alt="toggle-icon"
      class="dropdown__icon"
      :class="{ 'dropdown__icon--active': dropdownStatus }"
    />
  </div>
  <!-- Dropdown items container -->
  <div v-if="dropdownStatus" class="dropdown__items">
    <div
      v-for="item in items"
      :key="item.id"
      :class="{ 'dropdown--active': dropdownStatus }"
      class="dropdown__item"
      @click="toggleDropdown"
    >
      <div class="dropdown__icon-container">
        <img :src="item.iconSrc" />
      </div>
      <div>{{ item.text }}</div>
    </div>
  </div>
</template>

<script setup>
// import { onMounted, onBeforeUnmount } from 'vue';

// Data
const dropdownStatus = defineModel('dropdownStatus', {
  type: Boolean,
  default: false
});
const props = defineProps({
  label: {
    type: String,
    required: true
  },
  type: {
    type: String,
    default: 'simple',
    validator: value => ['simple', 'tools'].includes(value)
  },
  items: {
    type: Array,
    default: () => []
  },
  status: {
    type: Boolean
    // validator: value => ['active', 'inactive'].includes(value)
  }
});

// Methods
// Toggle dropdown
const toggleDropdown = event => {
  event.stopPropagation(); // Prevent event from bubbling up
  dropdownStatus.value = !dropdownStatus.value;
};
</script>

<style lang="scss" scoped>
@use '../../styles/abstract/variables';
@use '../../styles/abstract/functions';

.dropdown {
  display: flex;
  align-items: center;
  cursor: pointer;
  position: relative;

  &:hover {
    color: variables.$hover-active-color;
    .dropdown__icon {
      filter: brightness(0) saturate(100%) invert(63%) sepia(100%) saturate(500%) hue-rotate(0deg);
    }
  }

  &--active > &__label {
    color: variables.$hover-active-color;
  }

  &__icon {
    filter: brightness(0);

    &--active {
      filter: brightness(0) saturate(100%) invert(63%) sepia(100%) saturate(500%) hue-rotate(0deg);
    }
  }

  &__items {
    position: absolute;
    z-index: 106;
    top: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    padding: 1em;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    background-color: white;
    border-top: 3px solid variables.$hover-active-color;

    @media screen and (max-width: variables.$medium-screen) {
      position: relative;
      top: 0;
      left: 0;
      z-index: 0;
      box-shadow: none;
      border-top: none;
      margin-top: -1.8em;
      margin-bottom: -0.5em;
      padding: 1em 2.2em;
      background-color: none;
      grid-template-columns: 1fr;
      font-size: functions.rem(16);
      border-bottom: 2px solid #d9d9d9;
    }
  }

  &__item {
    display: flex;
    align-items: center;
    gap: 0.4em;
    padding: 0.2em 1em 0.3em 0.2em;
    min-width: 150px;
    // color: #292929;

    &:hover {
      color: variables.$hover-active-color-variant;

      & .dropdown__icon-container {
        background-color: #60aef6;
      }
    }
  }

  &__icon-container {
    background-color: #a6d1f9;
    display: flex;
    align-items: center;
    justify-items: center;
    border-radius: 5px;

    & img {
      min-height: 1.2em;
      padding: 0.2em;
    }
  }
}
</style>

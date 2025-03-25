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
import { onMounted, onBeforeUnmount } from 'vue';

// Data
// const dropdownOpen = ref(false);
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

// Close dropdown when clicking outside
const closeDropdown = event => {
  if (props.status && !event.target.closest('.dropdown')) {
    dropdownStatus.value = false;
  }
};

// Lifecycle hooks
// Add and remove event listeners with lifecycle hooks
onMounted(() => {
  document.addEventListener('click', closeDropdown);
  console.log('Dropdown mounted, items:', props.items.length);
});

onBeforeUnmount(() => {
  document.removeEventListener('click', closeDropdown);
  dropdownStatus.value = false;

  console.log('Dropdown unmounted');
});
</script>

<style lang="scss" scoped>
$hover-active-color: #ff8817;
$hover-active-color-variant: #0b89fe;
.dropdown {
  display: flex;
  align-items: center;
  cursor: pointer;
  position: relative;

  &:hover {
    color: $hover-active-color;
    .dropdown__icon {
      filter: brightness(0) saturate(100%) invert(63%) sepia(100%) saturate(500%) hue-rotate(0deg);
    }
  }

  &--active > &__label {
    color: $hover-active-color;
  }

  &__icon {
    filter: brightness(0);

    &--active {
      filter: brightness(0) saturate(100%) invert(63%) sepia(100%) saturate(500%) hue-rotate(0deg);
    }
  }

  &__items {
    position: absolute;
    z-index: 100;
    top: 100%;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    padding: 1em;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    background-color: white;
    border-top: 3px solid $hover-active-color;
  }

  &__item {
    display: flex;
    align-items: center;
    gap: 0.4em;
    padding: 0.2em 1em 0.3em 0.2em;

    &:hover {
      color: $hover-active-color-variant;

      img {
        background-color: #60aef6;
      }
    }

    & img {
      // filter: brightness(0);
      padding: 0.2em;
      max-width: 35px;
      border-radius: 5px;
      background-color: #98c9f7;
    }
  }
}
</style>

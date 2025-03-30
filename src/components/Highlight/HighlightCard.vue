<template>
  <div
    v-for="card in highlightCards"
    :key="card.id"
    :class="`step-${card.id}`"
    class="highlight__card"
  >
    <div class="highlight__card-flag" :class="`step-${card.id}`">Step {{ card.id }}.</div>
    <HighlightCase :cardId="card.id" />
    <div class="highlight__card-content" :class="`step-${card.id}`">
      <h3 class="highlight__card-title" :class="`step-${card.id}`">{{ card.title }}</h3>
      <p class="highlight__card-description">{{ card.description }}</p>
      <button class="highlight__card-button" :class="`step-${card.id}`">查看熱門工具</button>
    </div>
  </div>
</template>

<script setup>
import HighlightCase from './HighlightCase.vue';

defineProps({
  highlightCards: Array
});
</script>

<style lang="scss">
@use '@/styles/abstract/variables';
@use '@/styles/abstract/mixins';
@use '@/styles/abstract/functions';

.highlight__card {
  max-width: 800px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
  border-top-left-radius: 20px;
  border-bottom-right-radius: 20px;
  border-top-right-radius: 20px;
  border-bottom-left-radius: 0px;
  display: flex;
  position: relative;

  @media (max-width: variables.$large-screen) {
    flex-direction: column;
    max-width: 600px;
  }

  @media (max-width: variables.$medium-screen) {
    max-width: 350px;
  }

  &-flag.step-1 {
    background-color: #fcb33f;
    @include mixins.highlight-flag;
  }
  &-flag.step-2 {
    background-color: #55a3ec;
    @include mixins.highlight-flag;
  }

  &-content {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    padding: 1.5em;

    @media (max-width: variables.$large-screen) {
      align-items: center;
      margin: 0 auto;
    }

    & > p {
      margin: 0;
    }
  }
  &-title.step-1 {
    font-size: functions.rem(22);
    font-weight: 900;
    color: variables.$primary-btn-color;
  }
  &-title.step-2 {
    font-size: functions.rem(22);
    font-weight: 900;
    color: variables.$secondary-btn-color;
  }

  &-button.step-1 {
    @include mixins.gradient-button('primary');

    @media (max-width: variables.$large-screen) {
      background-color: #f8ca7f;
      color: #fff;
      border: none;
      border-radius: 50px;
    }
  }
  &-button.step-2 {
    @include mixins.gradient-button('secondary');

    @media (max-width: variables.$large-screen) {
      background-color: #72b1ed;
      color: #fff;
      border: none;
      border-radius: 50px;
    }
  }
}
</style>

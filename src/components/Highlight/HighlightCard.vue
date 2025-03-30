<template>
  <div class="highlight__card">
    <div class="highlight__card-flag">Step 1.</div>
    <HighlightCase />
    <div
      v-for="card in highlightCards"
      :key="card.id"
      class="highlight__card-content"
      :class="`step-${card.id}`"
    >
      <h3 class="highlight__card-title">{{ card.title }}</h3>
      <p class="highlight__card-description">{{ card.description }}</p>
      <button class="highlight__card-button">查看熱門工具</button>
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
@use '../../styles/abstract/variables';
@use '../../styles/abstract/mixins';
@use '../../styles/abstract/functions';

.highlight__card {
  max-width: 1000px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
  border-radius: 25px 15px 15px 15px;
  display: flex;
  position: relative;

  &-flag {
    max-width: 250px;
    position: absolute;
    top: -1px;
    left: -2px;
    font-size: functions.rem(22);
    padding: 0.4em 1.5em;
    background-color: #fcb33f;
    color: #fff;
    border-radius: 30px 0px 40px 0px;
  }

  &-content {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    padding: 1.5em;

    & > p {
      margin: 0;
    }
  }
  &-title {
    font-size: functions.rem(22);
    font-weight: 900;
    color: variables.$primary-btn-color;
  }
  &-button {
    @include mixins.gradient-button('primary');
  }
}
</style>

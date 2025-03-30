<template>
  <div class="highlight__card">
    <div class="highlight__card-flag">Step 1.</div>
    <div class="highlight__card-case"></div>
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
defineProps({
  highlightCards: Array
});
</script>

<style lang="scss">
@use '../../styles/abstract/variables';
@use '../../styles/abstract/mixins';
@use '../../styles/abstract/functions';

$primary-color: #ff8817;
$secondary-color: #55a3ec;
.highlight__card {
  max-width: 1000px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
  border-radius: 25px 15px 15px 15px;

  &-content {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    padding: 1.5em;
    // align-items: center;
    // justify-content: center;
    // gap: 20px;

    & > p {
      margin: 0;
    }
  }
  &-title {
    font-size: functions.rem(22);
    font-weight: 900;
    color: $primary-color;
  }
  &-button {
    @include mixins.gradient-button('primary');
  }
}
</style>

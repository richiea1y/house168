<template>
  <div v-for="card in highlightCards" :key="card.id" class="highlight-card">
    <div :class="`highlight-card__img card-bg-color-${card.id}`">
      <img :src="card.highlightImg" alt="highlight-img" />
    </div>
    <div class="highlight-card__text">
      <p class="highlight-card__text-title">
        {{ card.highlightTitle }}
      </p>
      <p
        v-for="content in card.highlightContent"
        :key="content"
        class="highlight-card__text-content"
      >
        {{ content }}
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  highlightCards: {
    type: Array
  }
});
</script>

<style lang="scss" scoped>
@use '../../styles/abstract/functions';
@use '../../styles/abstract/variables';

.highlight-card {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: functions.rem(20);
  width: calc(33.33% - functions.rem(18)); // Make cards take equal width with gap consideration
  min-width: functions.rem(300); // Minimum width to prevent too narrow cards
  padding: functions.rem(20) functions.rem(30);
  box-shadow: 0 6px 10px 0 rgba(0, 0, 0, 0.2);
  border-radius: 25px;
  background-image: linear-gradient(
    to right,
    rgba(255, 255, 255, 0.8) 0%,
    rgba(255, 255, 255, 0.7) 100%
  );

  @media (max-width: variables.$large-screen) {
    width: 100%; // Full width on smaller screens
    max-width: functions.rem(500); // Maximum width to maintain readability
  }

  &__img {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 15px;
    padding: functions.rem(10);
    // max-width: 40px;
    &.card-bg-color-1 {
      background-color: variables.$card-bg-color-1;
    }

    &.card-bg-color-2 {
      background-color: variables.$card-bg-color-2;
    }

    &.card-bg-color-3 {
      background-color: variables.$card-bg-color-3;
    }
    & > img {
      max-width: 40px;
    }
  }
  &__text {
    min-width: 0; // Allow text container to shrink
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    &-title {
      font-size: functions.rem(18);
      font-weight: 600;
      margin: functions.rem(5) 0;
      // color: variables.$primary-color;
    }

    &-content {
      font-size: functions.rem(12);
      margin: 0;
      text-overflow: ellipsis;
      // color: variables.$secondary-color;
    }
  }
}
</style>

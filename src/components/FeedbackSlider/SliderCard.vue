<template>
  <swiper-slide class="slider__card">
    <div class="slider-card__author">
      <div class="slider-card__author-avatar">
        <img :src="feedback.avatar" :alt="feedback.name" class="slider-card__author-img" />
      </div>
      <div class="slider-card__author-name">
        <p>{{ feedback.name }}</p>
      </div>
      <div class="slider-card__author-role">
        <p>
          {{ feedback.position }}
        </p>
      </div>
    </div>
    <div class="slider-card__content">
      <div class="slider-card__content-icon">
        <img src="@/assets/images/quote-left.png" alt="Quote" class="slider-card__quote-icon" />
      </div>
      <div class="slider-card__content-text">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt
          ut labore et dolore magna aliqua
        </p>
      </div>
    </div>
  </swiper-slide>
</template>

<script setup>
defineProps({
  feedback: {
    type: Object
  }
});
</script>

<style lang="scss">
@use '@/styles/abstract/functions';
@use '@/styles/abstract/variables';

.slider__card {
  display: flex;
  padding: 2em 2em;
  margin: 1em 1em;
  background-color: #fff;
  box-shadow: 0 5px 5px 0 rgba(0, 0, 0, 0.3);
  border-radius: 25px;
  max-width: 360px;
  // position: relative;

  @media screen and (max-width: variables.$large-screen) {
    flex-direction: column;
    max-width: 220px;
    padding: 1em;
    margin: 0.5em;
    gap: 0.5em;
  }
}

.slider-card__author {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3em;

  & p {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    color: #0b89fe;
  }

  &-img {
    max-width: 120px;
    @media screen and (max-width: variables.$large-screen) {
      max-width: 70px;
    }
  }

  &-name {
    font-size: functions.rem(16);
    font-weight: 600;
    @media screen and (max-width: variables.$large-screen) {
      font-size: functions.rem(12);
      font-weight: 500;
    }
  }

  &-role {
    font-size: functions.rem(14);
    font-weight: 500;
    @media screen and (max-width: variables.$large-screen) {
      font-size: functions.rem(12);
    }
  }
}

.slider-card__content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 0em;
  margin: 0 1.5em;

  &-icon {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0.7em;
    background-color: #0b89fe;
    border-radius: 50%;
    @media screen and (max-width: variables.$large-screen) {
      padding: 0.2em;
    }

    & > img {
      max-width: 1em;
      @media screen and (max-width: variables.$large-screen) {
        max-width: 0.5em;
      }
    }
  }

  &-text {
    font-family: Arial, Helvetica, sans-serif;
    font-size: functions.rem(14);
    font-weight: 400;
    text-align: center;
    color: #3c3c3c;
    line-height: 1.4em;

    @media screen and (max-width: variables.$large-screen) {
      font-size: functions.rem(12);
    }
  }
}
</style>

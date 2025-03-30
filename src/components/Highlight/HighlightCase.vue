<template>
  <div v-if="cardId === 1" class="highlight__card-case" :class="`step-${cardId}`">
    <img
      src="@/assets/images/highlight-before.png"
      alt="house168 行銷工具"
      class="interior-image1"
    />
    <img src="@/assets/images/double-arrow.png" alt="house168 行銷工具" />
    <img
      src="@/assets/images/highlight-after.png"
      alt="house168 行銷工具"
      class="interior-image2"
    />
  </div>
  <div v-else class="highlight__card-case" :class="`step-${cardId}`">
    <img src="@/assets/images/website-page.png" alt="house168 行銷工具" class="website-image" />
  </div>
</template>

<script setup>
defineProps({
  cardId: Number
});
</script>

<style lang="scss">
@use '@/styles/abstract/variables';

.highlight__card-case {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  padding: 1em 2em;
  border-top-left-radius: 20px;
  border-bottom-right-radius: 30px;
  background: linear-gradient(
    135deg,
    rgba(214, 250, 252, 1) 0%,
    rgba(254, 222, 163, 1) 64%,
    rgba(255, 206, 130, 1) 100%
  );

  &.step-1 {
    img {
      max-width: 160px;

      @media (max-width: variables.$medium-screen) {
        max-width: 100px;
      }
    }
    @media (max-width: variables.$large-screen) {
      padding: 3em 3em;
    }
    @media (max-width: variables.$medium-screen) {
      padding: 2em 1em;
    }
  }

  &.step-2 {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 1em 2em;
    img {
      max-width: 400px;

      @media (max-width: variables.$medium-screen) {
        max-width: 300px;
      }
    }
    @media (max-width: variables.$large-screen) {
      padding: 3em 3em;
    }
    @media (max-width: variables.$medium-screen) {
      padding: 2em 1em;
    }
  }

  &.step1,
  &.step2 {
  }
}
</style>

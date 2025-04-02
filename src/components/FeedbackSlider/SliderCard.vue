<template>
  <div class="swiper-slide" v-for="feedback in feedback" :key="feedback.id">
    <div class="slider-card__content">
      <div class="slider-card__content-text">
        <p>{{ feedback.content }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  feedback: {
    type: Array,
    required: true
  }
});
</script>

<style lang="scss"></style>

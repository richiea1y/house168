<template>
  <div class="feature-card">
    <div class="card-icon">
      <img :src="feature.icon" :alt="feature.title" />
    </div>
    <h3 class="card-title">{{ feature.title }}</h3>
    <div class="card-description">
      <p v-for="(line, index) in feature.description" :key="index">{{ line }}</p>
    </div>
    <div class="card-footer">
      <a href="#" class="learn-more">瞭解更多 <span class="arrow"></span></a>
    </div>
  </div>
</template>

<script setup>
defineProps({
  feature: {
    type: Object,
    required: true
  }
});
</script>

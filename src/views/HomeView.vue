<script setup>
import TheHeader from '@/components/TheHeader.vue';
import TheHero from '@/components/TheHero.vue';
// import TheFooter from '@/components/TheFooter.vue';
// import FeatureGrid from '@/components/FeatureGrid.vue';
// import ServiceSlider from '@/components/ServiceSlider.vue';
// import PromotionBanner from '@/components/PromotionBanner.vue';
// import TestimonialSlider from '@/components/TestimonialSlider.vue';
// import PartnerSlider from '@/components/PartnerSlider.vue';
// import HighlightSection from '@/components/HighlightSection.vue';
</script>

<template>
  <div id="app">
    <TheHeader />
    <TheHero />
    <FeatureGrid />
    <!-- <ServiceSlider /> -->
    <!-- <PromotionBanner /> -->
    <!-- <TestimonialSlider /> -->
    <!-- <PartnerSlider /> -->
    <!-- <HighlightSection /> -->
    <!-- <TheFooter /> -->
  </div>
</template>

<style lang="scss">
@use '@/styles/components/_navbar.scss';
</style>

<script setup>
import TheHeader from '@/components/TheHeader.vue';
import TheHero from '@/components/TheHero.vue';
import FeatureGrid from '@/components/FeatureGrid.vue';
import PromotionBanner from '@/components/PromotionBanner.vue';
import TestimonialSlider from '@/components/TestimonialSlider.vue';
import HighlightSection from '@/components/HighlightSection.vue';
import TheFooter from '@/components/TheFooter.vue';
</script>

<template>
  <div id="app">
    <TheHeader />
    <TheHero />
    <FeatureGrid />
    <PromotionBanner />
    <TestimonialSlider />
    <HighlightSection />
    <TheFooter />
  </div>
</template>

<style lang="scss">
@use '../styles/main.scss';
</style>

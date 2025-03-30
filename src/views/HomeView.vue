<script setup>
import Navbar from '@/components/Navbar/Navbar.vue';
import TheHero from '@/components/Hero/TheHero.vue';
import FeatureTools from '@/components/FeatureTools/FeatureTools.vue';
import PromotionBanner from '@/components/PromotionBanner.vue';
import TestimonialSlider from '@/components/TestimonialSlider.vue';
import HighlightSection from '@/components/HighlightSection.vue';
import TheFooter from '@/components/TheFooter.vue';
</script>

<template>
  <div id="app">
    <Navbar />
    <TheHero />
    <FeatureTools />
    <PromotionBanner />
    <TestimonialSlider />
    <HighlightSection />
    <TheFooter />
  </div>
</template>

<style lang="scss">
@use '../styles/main.scss';
</style>

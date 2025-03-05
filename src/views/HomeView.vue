<script setup>
import TheHeader from '@/components/layout/TheHeader.vue';
// import TheMain from '../layout/TheMain.vue';
// import TheFooter from '../layout/TheFooter.vue';
// import HeroBanner from '../components/HeroBanner.vue';
// import FeatureGrid from '../components/FeatureGrid.vue';
// import ServiceSlider from '../components/ServiceSlider.vue';
// import PromotionBanner from '../components/PromotionBanner.vue';
// import TestimonialSlider from '../components/TestimonialSlider.vue';
// import PartnerSlider from '../components/PartnerSlider.vue';
// import HighlightSection from '../components/HighlightSection.vue';
</script>

<template>
  <div id="app">
    <TheHeader />
    <TheMain>
      <!-- Home page content sections -->
      <HeroBanner />
      <FeatureGrid />
      <ServiceSlider />
      <PromotionBanner />
      <TestimonialSlider />
      <PartnerSlider />
      <HighlightSection />
    </TheMain>
    <TheFooter />
  </div>
</template>

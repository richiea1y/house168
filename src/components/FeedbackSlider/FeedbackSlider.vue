<template>
  <div class="feedback">
    <div class="feedback-header">
      <p>––&emsp;&ensp;與我們合作的夥伴都說&ensp;&emsp;––</p>
    </div>

    <div class="slider__container">
      <!-- Slider main container -->
      <swiper-container
        :navigation="{
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }"
      >
        <SliderCard v-for="item in feedback" :key="item.id" :feedback="item" />
      </swiper-container>
    </div>
    <div class="swiper-btn">
      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>
    </div>
    <div class="agent-icon-marquee">
      <div class="marquee-content">
        <!-- First set of images -->
        <img
          v-for="(img, index) in marqueeImages"
          :key="index"
          :src="img"
          alt=""
          class="agent-icon"
        />
        <!-- Duplicate set of images for seamless loop -->
        <img
          v-for="(img, index) in marqueeImages"
          :key="'duplicate-' + index"
          :src="img"
          alt=""
          class="agent-icon"
        />
      </div>
    </div>
  </div>
</template>
avatar

<script setup>
import { ref } from 'vue';
import SliderCard from '@/components/FeedbackSlider/SliderCard.vue';
import 'swiper/css';
import 'swiper/css/navigation';
// import 'swiper/swiper-bundle.css'; // import Swiper styles

// import function to register Swiper custom elements
import { register } from 'swiper/element/bundle';
register();

// Define testimonials data
const feedback = ref([
  {
    id: 1,
    name: 'Mandy Oza',
    position: 'Xyz Company Ceo',
    avatar: new URL('@/assets/images/partner1.png', import.meta.url).href
  },
  {
    id: 2,
    name: 'Jessica Lin',
    position: 'Xyz Company Ceo',
    avatar: new URL('@/assets/images/partner2.png', import.meta.url).href
  },
  {
    id: 3,
    name: 'David Chen',
    position: 'Xyz Company Ceo',
    avatar: new URL('@/assets/images/partner3.png', import.meta.url).href
  },
  {
    id: 4,
    name: 'Sarah Wang',
    position: 'Xyz Company Ceo',
    avatar: new URL('@/assets/images/partner4.png', import.meta.url).href
  },
  {
    id: 5,
    name: 'Michael Huang',
    position: 'Xyz Company Ceo',
    avatar: new URL('@/assets/images/partner5.png', import.meta.url).href
  }
]);

// Define marquee images
const marqueeImages = ref([
  new URL('@/assets/images/icon/agent-logo.png', import.meta.url).href,
  new URL('@/assets/images/icon/agent-logo.png', import.meta.url).href
]);
</script>

<style lang="scss">
@use '@/styles/layout/_feedback.scss';

// Add these styles directly in the component
:root {
  --swiper-navigation-size: 20px; // Control arrow size
  --swiper-theme-color: #fff; // Control arrow color
}

.swiper-button-next,
.swiper-button-prev {
  &::after {
    background: none !important;
    border-radius: 0 !important;
    box-shadow: none !important;
  }
}
</style>

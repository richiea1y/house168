<template>
  <!-- <div class="testimonial-header">
    <p>––&emsp;&ensp;與我們合作的夥伴都說&ensp;&emsp;––</p>
  </div> -->

  <!-- Slider main container -->
  <div class="swiper feedbackSlider" :modules="[SwiperNavigation]">
    <!-- Additional required wrapper -->
    <div class="swiper-wrapper">
      <!-- Slides -->
      <div class="swiper-slide">Slide 1</div>
      <div class="swiper-slide">Slide 2</div>
      <div class="swiper-slide">Slide 3</div>
      <!-- <SliderCard :feedback="testimonials" /> -->
      ...
    </div>
    <!-- navigation buttons -->
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
  </div>
</template>

<script setup>
// import { ref } from 'vue';
// import SliderCard from '@/components/FeedbackSlider/SliderCard.vue';
import Swiper from 'swiper';
import { Navigation as SwiperNavigation } from 'swiper/modules';

import 'swiper/css';
import 'swiper/css/navigation';

new Swiper('.feedbackSlider', {
  modules: [SwiperNavigation],
  // spaceBetween: 30,
  pagination: {
    el: '.swiper-pagination',
    clickable: true
  }
});

// Define testimonials data
// const testimonials = ref([
//   {
//     content:
//       'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
//     name: 'Mandy Oza',
//     position: 'Xyz Company Ceo',
//     avatar: new URL('@/assets/images/partner1.png', import.meta.url).href
//   },
//   {
//     content:
//       'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
//     name: 'Jessica Lin',
//     position: 'ABC Company Manager',
//     avatar: new URL('@/assets/images/partner2.png', import.meta.url).href
//   },
//   {
//     content:
//       'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
//     name: 'David Chen',
//     position: 'DEF Company Director',
//     avatar: new URL('@/assets/images/partner3.png', import.meta.url).href
//   },
//   {
//     content:
//       'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
//     name: 'Sarah Wang',
//     position: 'GHI Company Founder',
//     avatar: new URL('@/assets/images/partner4.png', import.meta.url).href
//   },
//   {
//     content:
//       'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
//     name: 'Michael Huang',
//     position: 'JKL Organization Head',
//     avatar: new URL('@/assets/images/partner5.png', import.meta.url).href
//   }
// ]);
</script>

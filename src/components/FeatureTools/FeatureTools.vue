<template>
  <div class="feature-grid-container">
    <div class="feature-header">
      <p class="feature-header-title">熱門推薦工具</p>
      <p class="feature-header-description">
        透過house168的房屋變裝服務，我們利用最新的AI技術，將空置或髒亂的房屋重新裝扮，為您呈現出煥然一新的風貌，無論是全新的成屋還是中古房屋，我們能夠重新設計裝潢，讓每個空間焕然一新。這不僅能吸引更多潛在買家的注意，還能加速房屋成交的速度，讓您的房地產業務更上一層樓。
      </p>
    </div>

    <div class="feature-carousel">
      <div class="carousel-container">
        <swiper-container
          :slides-per-view="slidesPerView"
          :slides-per-group="slidesPerView"
          :space-between="20"
          :loop="true"
          :loopFillGroupWithBlank="true"
          :navigation="{
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
            disabledClass: 'swiper-button-disabled'
          }"
          :pagination="false"
          :breakpoints="swiperBreakpoints"
          class="mySwiper"
        >
          <swiper-slide v-for="(feature, index) in features" :key="index">
            <FeatureCard :feature="feature" />
          </swiper-slide>
        </swiper-container>

        <div class="swiper-btn">
          <div class="swiper-button-prev"></div>
          <div class="swiper-button-next"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import FeatureCard from './FeatureCard.vue';

// Import Swiper styles
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

import { register } from 'swiper/element/bundle';
register();

// Responsive settings
const windowWidth = ref(window.innerWidth);

onMounted(() => {
  window.addEventListener('resize', () => {
    windowWidth.value = window.innerWidth;
  });
});

const slidesPerView = computed(() => {
  if (windowWidth.value < 640) return 1;
  if (windowWidth.value < 960) return 2;
  return 4;
});

const swiperBreakpoints = {
  320: {
    slidesPerView: 1,
    spaceBetween: 15,
    slidesPerGroup: 1
  },
  640: {
    slidesPerView: 2,
    spaceBetween: 15,
    slidesPerGroup: 2
  },
  960: {
    slidesPerView: 3,
    spaceBetween: 15,
    slidesPerGroup: 3
  },
  1100: {
    slidesPerView: 4,
    spaceBetween: 15,
    slidesPerGroup: 4
  }
};

// Feature data
const features = [
  {
    icon: new URL('@/assets/images/feature_icon1.png', import.meta.url).href,
    title: '房屋整裝工具',
    description: ['舊房翻新煥然一新', '強化賣方競爭優勢', '吸引買家，加速成交']
  },
  {
    icon: new URL('@/assets/images/feature_icon2.png', import.meta.url).href,
    title: '智能銷售報告書',
    description: ['智能整合房產報告書', '秀出個人專業', '提升服務價值']
  },
  {
    icon: new URL('@/assets/images/feature_icon3.png', import.meta.url).href,
    title: '建案行銷執行',
    description: ['一站式整合包裝', '專業品質，建商首選', '為您贏得市場']
  },
  {
    icon: new URL('@/assets/images/feature_icon4.png', import.meta.url).href,
    title: '浮水印工具',
    description: ['浮水印智能添加', '輕鬆處理', '專業無負擔']
  },
  {
    icon: new URL('@/assets/images/feature_icon1.png', import.meta.url).href,
    title: '房屋整裝工具2',
    description: ['舊房翻新煥然一新', '強化賣方競爭優勢', '吸引買家，加速成交']
  },
  {
    icon: new URL('@/assets/images/feature_icon2.png', import.meta.url).href,
    title: '智能銷售報告書2',
    description: ['智能整合房產報告書', '秀出個人專業', '提升服務價值']
  },
  {
    icon: new URL('@/assets/images/feature_icon3.png', import.meta.url).href,
    title: '建案行銷執行2',
    description: ['一站式整合包裝', '專業品質，建商首選', '為您贏得市場']
  },
  {
    icon: new URL('@/assets/images/feature_icon4.png', import.meta.url).href,
    title: '浮水印工具2',
    description: ['浮水印智能添加', '輕鬆處理', '專業無負擔']
  }
];
</script>

<style lang="scss">
@use '@/styles/layout/_feature.scss';
</style>

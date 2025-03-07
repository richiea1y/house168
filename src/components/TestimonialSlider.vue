<template>
  <div class="testimonial-slider">
    <div class="testimonial-header">
      <p>––&emsp;&ensp;與我們合作的夥伴都說&ensp;&emsp;––</p>
    </div>
    <div class="slider-container">
      <swiper
        :modules="[SwiperNavigation, SwiperPagination]"
        :slides-per-view="1"
        :breakpoints="{
          768: {
            slidesPerView: 2,
            spaceBetween: 20
          },
          1024: {
            slidesPerView: 3,
            spaceBetween: 50
          }
        }"
        :space-between="140"
        :navigation="{
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }"
        :pagination="{ clickable: true }"
        :autoplay="{
          delay: 5000,
          disableOnInteraction: false
        }"
        :loop="true"
        class="testimonial-swiper"
      >
        <swiper-slide v-for="(testimonial, index) in testimonials" :key="index">
          <div class="testimonial-card">
            <div class="testimonial-author">
              <img :src="testimonial.avatar" :alt="testimonial.name" class="testimonial-avatar" />
              <div class="testimonial-author-info">
                <h4 class="testimonial-author-name">{{ testimonial.name }}</h4>
                <p class="testimonial-author-position">{{ testimonial.position }}</p>
              </div>
            </div>
            <div class="testimonial-content">
              <div class="testimonial-quote">
                <img
                  src="@/assets/images/quote-left.png"
                  alt="Quote"
                  class="testimonial-quote-icon"
                />
              </div>
              <p>{{ testimonial.content }}</p>
            </div>
          </div>
        </swiper-slide>
      </swiper>

      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>
    </div>
    <div class="agent-icon-marquee"></div>
  </div>
</template>

<script>
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

export default {
  name: 'TestimonialSlider',
  components: {
    Swiper,
    SwiperSlide
  },
  setup() {
    const SwiperNavigation = Navigation;
    const SwiperPagination = Pagination;
    const SwiperAutoplay = Autoplay;

    const testimonials = ref([
      {
        content:
          'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
        name: 'Mandy Oza',
        position: 'Xyz Company Ceo',
        avatar: new URL('@/assets/images/partner1.png', import.meta.url).href
      },
      {
        content:
          'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
        name: 'Jessica Lin',
        position: 'ABC Company Manager',
        avatar: new URL('@/assets/images/partner2.png', import.meta.url).href
      },
      {
        content:
          'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
        name: 'David Chen',
        position: 'DEF Company Director',
        avatar: new URL('@/assets/images/partner3.png', import.meta.url).href
      },
      {
        content:
          'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
        name: 'Sarah Wang',
        position: 'GHI Company Founder',
        avatar: new URL('@/assets/images/partner4.png', import.meta.url).href
      },
      {
        content:
          'Lorem Ipsum Dolor Sit Amet, Consectetur Adipiscing Elit, Sed Do Eiusmod Tempor Incididunt Ut Labore Et Dolore Magna Aliqua',
        name: 'Michael Huang',
        position: 'JKL Organization Head',
        avatar: new URL('@/assets/images/partner5.png', import.meta.url).href
      }
    ]);

    return {
      testimonials,
      SwiperNavigation,
      SwiperPagination,
      SwiperAutoplay
    };
  }
};
</script>

<style lang="scss">
@use '@/styles/components/_testimonial.scss';
</style>

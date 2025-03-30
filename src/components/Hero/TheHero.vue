<template>
  <div class="hero-container">
    <div class="hero-content1-container">
      <div class="content1-slogan-container">
        <div class="content1-slogan-text">
          <p>專業，安心，信任！</p>
          <img src="@/assets/images/icon/slogan-logo.svg" alt="Logo" />
          <p>助您業績成長的最佳夥伴！</p>
        </div>
        <div class="content1-slogan-btn">
          <button class="slogan-btn1">瀏覽強大工具</button>
          <button class="slogan-btn2">168房屋銷售網</button>
        </div>
      </div>
      <div class="content1-video-container">
        <div class="video-container">
          <img src="@/assets/images/hero-img.jpg" alt="hero-img" />
          <div class="play-btn-container">
            <img src="@/assets/images/icon/play-btn.svg" alt="play-btn" />
          </div>
        </div>
      </div>
    </div>
    <div class="hero-content2-container">
      <HighlightCard :highlight-cards="hightlightCards" />
    </div>
    <div class="hero-content3-container">
      <div class="tools-img-container">
        <div class="tools-img1">
          <img src="@/assets/images/before-interior.png" alt="" />
        </div>
        <div class="tools-img2">
          <img src="@/assets/images/after-interior.png" alt="" />
        </div>
        <div class="tools-img3">
          <img src="@/assets/images/before-interior-flag.png" alt="" />
        </div>
        <div class="tools-img4">
          <img src="@/assets/images/after-interior-flag.png" alt="" />
        </div>
      </div>
      <div class="tools-intro-container">
        <div class="tools-intro1">
          <div class="tools-intro1-title">
            <p>主打工具-房屋變裝</p>
            <p>房仲成交神器</p>
          </div>
          <div class="tools-intro1-content">
            <p>透過house168的房屋變裝服務，</p>
            <p>我們利用最新的AI技術，</p>
            <p>將空置或髒亂的房屋重新裝扮，</p>
            <p>為您呈現出煥然一新的風貌</p>
            <p>無論是全新的成屋還是中古房屋，</p>
            <p>我們能夠重新設計裝潢，</p>
            <p>讓每個空間焕然一新。</p>
            <p>這不僅能吸引更多潛在買家的注意，</p>
            <p>還能加速房屋成交的速度，</p>
            <p>讓您的房地產業務更上一層樓。</p>
          </div>
        </div>
        <button class="tools-intro2">瞭解更多</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import HighlightCard from '@/components/Hero/HighlightCard.vue';

const hightlightCards = ref([
  {
    id: 1,
    highlightImg: '/src/assets/images/content2-img1.png',
    highlightTitle: '創新科技 引領未來',
    highlightContent: [
      'house168，不斷追求創新技術，',
      '引領未來趨勢，為您提供卓越服務，',
      '成就房仲夥伴的交易目標。'
    ]
  },
  {
    id: 2,
    highlightImg: '/src/assets/images/content2-img2.png',
    highlightTitle: '儲值點數 終生有效',
    highlightContent: ['儲值點數，不受時間限制，', '長期使用我們的服務，', '充分發揮您的業務潛力。']
  },
  {
    id: 3,
    highlightImg: '/src/assets/images/content2-img3.png',
    highlightTitle: '專業服務 成就卓越',
    highlightContent: [
      'house168，您成功的一大助力，',
      '資訊整合、深度服務，',
      '有效幫助成為您最信賴的合作夥伴。'
    ]
  }
]);
</script>

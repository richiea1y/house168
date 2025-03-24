<template>
  <div class="promotion-banner">
    <!-- Decorative elements - coins -->
    <img src="@/assets/images/coin1.png" alt="" class="decoration coin-1" />
    <img src="@/assets/images/coin2.png" alt="" class="decoration coin-2" />
    <img src="@/assets/images/coin3.png" alt="" class="decoration coin-3" />
    <img src="@/assets/images/coin4.png" alt="" class="decoration coin-4" />
    <img src="@/assets/images/coin5.png" alt="" class="decoration coin-5" />
    <img src="@/assets/images/coin6.png" alt="" class="decoration coin-6" />

    <!-- Decorative elements - left triangles -->
    <img src="@/assets/images/triangle1.png" alt="" class="decoration triangle-1 left-triangle" />
    <img src="@/assets/images/triangle2.png" alt="" class="decoration triangle-2 left-triangle" />

    <!-- Decorative elements - right triangles -->
    <img src="@/assets/images/triangle1.png" alt="" class="decoration triangle-3 right-triangle" />
    <img src="@/assets/images/triangle2.png" alt="" class="decoration triangle-4 right-triangle" />

    <!-- Decorative elements - left waves -->
    <img src="@/assets/images/wave1.png" alt="" class="decoration wave-1" />
    <img src="@/assets/images/wave2.png" alt="" class="decoration wave-2" />

    <!-- Decorative elements - right waves -->
    <img src="@/assets/images/wave1.png" alt="" class="decoration wave-3" />
    <img src="@/assets/images/wave2.png" alt="" class="decoration wave-4" />

    <div class="promotion-left">
      <img
        src="@/assets/images/shopping.png"
        alt="Shopping illustration"
        class="shopping-illustration"
      />
    </div>
    <div class="promotion-right">
      <p class="promotion-subtitle">現在儲值點數最高享</p>
      <p class="promotion-title">80% OFF</p>
      <p class="promotion-description">買越多賺越多！</p>
      <button class="promotion-button">立即查看方案</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PromotionBanner'
};
</script>

<style lang="scss" scoped>
@use '@/styles/layout/_promotion.scss';
</style>

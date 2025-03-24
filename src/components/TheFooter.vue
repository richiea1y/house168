<template>
  <section class="footer">
    <div class="footer-container">
      <div class="company-content footer-content">
        <div class="company-logo">
          <img src="@/assets/images/footer_logo.png" alt="logo" />
        </div>
        <div class="company-description">
          <p>雲弈智能科技股份有限公司</p>
          <p>電話：02-7713-6650</p>
          <p>郵件：Mail@gmail.com</p>
          <p>統編：93522665</p>
          <p>地址：104台北市中山區復興北路344號7樓之1</p>
        </div>
      </div>
      <div class="service-content footer-content">
        <p class="footer-header">服務項目</p>
        <div class="service-item">
          <p>房屋變裝工具</p>
          <p>浮水印工具</p>
          <p>智能銷售報告書</p>
          <p>LINE貼圖</p>
          <p>建商行銷執行</p>
          <p>顧問型影音</p>
        </div>
      </div>
      <div class="contact-content footer-content">
        <p class="footer-header">加入官方 LINE</p>
        <img src="@/assets/images/line.png" alt="" />
      </div>
      <div class="follow-us-content footer-content">
        <p class="footer-header">關注我們</p>
        <div class="follow-us-item">
          <img src="@/assets/images/ig.png" alt="" />
          <img src="@/assets/images/fb.png" alt="" />
          <img src="@/assets/images/yt.png" alt="" />
        </div>
      </div>
    </div>
    <div class="copyright-content footer-content">
      <p>house168.com©all right reserve</p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'TheFooter'
};
</script>

<style lang="scss" scoped>
@use '@/styles/layout/_footer.scss';
</style>

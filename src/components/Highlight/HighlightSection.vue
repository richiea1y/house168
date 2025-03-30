<template>
  <div class="highlight__section">
    <!-- Old Code -->
    <div class="highlight-header">
      <h2 class="highlight-title">讓我們為您提供助力</h2>
      <p class="highlight-description">
        house168致力於為房屋買賣市場提供更優質的環境，我們的線上服務分為兩大平台，
      </p>
      <p class="highlight-description">您可以依序使用，或是按照您的需求決定！</p>
    </div>
    <HighlightCard :highlightCards="highlightCards" />
  </div>
</template>

<script setup>
import HighlightCard from './HighlightCard.vue';

const highlightCards = [
  {
    id: 1,
    title: 'house168 行銷工具',
    description:
      '若您想提高房屋銷售的成交可能性、增加物件受青睞的機率，您可以使用house168工具網所提供的強大工具！'
  },
  {
    id: 2,
    title: 'house168 房屋交易網',
    description:
      '若您已經準備好一切，您可以前往house168房屋交易平台，我們將協助您更快更輕鬆找到優秀的買家與賣家！'
  }
];
</script>

<style lang="scss">
@use '@/styles/abstract/variables';
@use '@/styles/abstract/mixins';
@use '@/styles/layout/_highlight.scss';
.highlight__card.step-1 {
  margin-right: 14em;
}
.highlight__card.step-2 {
  margin-left: 14em;
}

@media (max-width: variables.$large-screen) {
  .highlight-description {
    max-width: 350px;
  }

  .highlight__card.step-1 {
    margin-right: 0;
  }
  .highlight__card.step-2 {
    margin-left: 0;
  }
}
</style>

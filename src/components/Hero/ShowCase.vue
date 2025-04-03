<template>
  <div class="hero__tranformation-showcase">
    <div class="showcase__before">
      <div class="showcase__before-label">
        <img src="@/assets/images/before-interior-flag.png" alt="" />
      </div>
      <div class="showcase__before-img">
        <img src="@/assets/images/before-interior.png" alt="" />
      </div>
    </div>
    <div class="showcase__after">
      <div class="showcase__after-img">
        <img src="@/assets/images/after-interior.png" alt="" />
      </div>
      <div class="showcase__after-label">
        <img src="@/assets/images/after-interior-flag.png" alt="" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use '../../styles/abstract/functions';
@use '../../styles/abstract/mixins';
// .hero__tranformation-showcase {
// position: relative;
// max-width: 500px;

.showcase__before {
  z-index: 1;
  @include mixins.showcase-container('before');
}

.showcase__after {
  z-index: 2;
  margin-top: -4em;
  @include mixins.showcase-container('after');
}
</style>

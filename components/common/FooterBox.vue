<template>
  <div class="footer-box d-flex flex-column justify-content-between w-100">
    <div class="d-flex mb-3 flex-column">
      <div class="d-flex justify-content-center align-items-center">
        <NuxtLink to="" class="neoguri-font-93 color-neoguri-darkgray">커뮤니티 규칙</NuxtLink>
        <span class="divider mx-2"></span>
        <NuxtLink to="" class="neoguri-font-93 color-neoguri-darkgray">이용약관</NuxtLink>
      </div>
      <div class="d-flex justify-content-center align-items-center">
        <NuxtLink to="" class="neoguri-font-93 color-neoguri-darkgray">회사소개</NuxtLink>
        <span class="divider mx-2"></span>
        <NuxtLink to="" class="neoguri-font-93 color-neoguri-darkgray">제휴제안</NuxtLink>
        <span class="divider mx-2"></span>
        <NuxtLink to="" class="neoguri-font-93 color-neoguri-darkgray">개인정보처리방침</NuxtLink>
      </div>
    </div>

    <div class="d-flex justify-content-center">
      <img class="neoguri-logo w-100 h-100" src="/img/neoguri-logo.png" alt="너구리소굴 로고"/>
    </div>
  </div>
</template>

<script>

import Vue from "vue";

export default Vue.extend({
  name: 'FooterBox',
  props: {

  },
  methods: {
  }
})

</script>

<style scoped>
  .footer-box {
    padding: 21px 0 28px 0;
    background-color: #E0E0E0;
  }

  .neoguri-logo {
    max-width: 120px;
  }

  .divider {
    height: 9px;
    border-right: 1px solid #979797;
  }
</style>

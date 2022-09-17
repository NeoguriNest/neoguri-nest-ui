<template>
  <div class="d-flex flex-column">
    <HeaderBox title="로그인" />

    <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">
      <NeoguriBanner />
      <div class="d-flex flex-column text-center">
        <h2 class="neoguri-font-weight-700 color-neoguri-title pb-4 mb-0">너구리소굴</h2>
        <p class="neoguri-font-weight-400 fs-6 mb-0">너구리소굴에 방문하신 것을 진심으로 환영합니다.</p>
      </div>

      <div class="pt-4">
        <LoginBox />
      </div>

      <div class="pt-4">
        <RegisterBox />
      </div>

      <div class="pt-4">
        <SnsLoginBox />
      </div>

    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HeaderBox from '~/components/common/HeaderBox.vue'
import NeoguriBanner from '~/components/common/banners/NeoguriBanner.vue'
import LoginBox from '@/components/LoginBox.vue'
import RegisterBox from '@/components/RegisterBox.vue'
import SnsLoginBox from '@/components/SnsLoginBox.vue'

export default Vue.extend({
  name: 'LoginPage',
  components: {
    HeaderBox,
    NeoguriBanner,
    LoginBox,
    RegisterBox,
    SnsLoginBox
  }
})
</script>

<style scoped>
</style>

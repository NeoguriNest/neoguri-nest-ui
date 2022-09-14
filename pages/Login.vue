<template>
  <div class="d-flex flex-column">
    <HeaderBox title="로그인" />

    <div class="d-flex flex-column px-3">
      <div class="d-flex w-100 py-4">
        <img class="w-100 h-100" src="/img/intro-banner.png" alt="반갑다구리 배너"/>

      </div>


      <LoginBox />
    </div>
  </div>

</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'LoginPage'
})
</script>
<style scoped>
  .login-container {
    padding: 0 20px;
  }
</style>

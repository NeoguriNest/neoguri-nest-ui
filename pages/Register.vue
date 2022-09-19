<template>
  <div class="d-flex flex-column">
    <HeaderBox title="너구리단 가입" />

    <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">

      <div class="pt-8">
        <LoginIdInput name="login_id" title="아이디" required />
      </div>

      <div class="pt-8">
        <PasswordInput name="password" title="비밀번호" required />
      </div>

      <div class="pt-8">
        <PasswordInput name="password_confirm" title="비밀번호 확인" required />
      </div>

      <div class="pt-8">
        <EmailInput name="email" title="이메일" required />
      </div>

    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HeaderBox from '@/components/common/HeaderBox.vue'
import LoginIdInput from '~/components/common/inputs/LoginIdInput.vue'
import PasswordInput from '~/components/common/inputs/PasswordInput.vue'
import EmailInput from '~/components/common/inputs/EmailInput.vue'

export default Vue.extend({
  name: 'RegisterPage',
  components: {
    HeaderBox,
    LoginIdInput,
    PasswordInput,
    EmailInput
  }
})
</script>

<style scoped>
</style>

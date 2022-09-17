<template>
  <div class="d-flex flex-column">
    <div class="input-group flex-column mb-3">
      <input type="text" placeholder="아이디" class="py-3 px-4 mb-2" />
      <input type="text" placeholder="비밀번호" class="py-3 px-4" />
    </div>
    <div class="d-flex mb-4">
      <label class="d-flex align-items-center mb-0">
        <input type="checkbox" name="maintain_login" />
        <p class="ml-2 mb-0">로그인 상태 유지</p>
      </label>
    </div>
    <div class="login-buttons d-flex flex-column">
      <button class="neoguri-btn-style-1 py-3 border-0">너구리소굴 로그인</button>
    </div>
  </div>
</template>

<script>
import { Component } from "nuxt-property-decorator";
import Vue from "vue";

@Component({})
export default class LoginBox extends Vue {
}
</script>

<style scoped>
  input[type=text] {
    border: 1px solid #DFDFDF;
  }

  input::placeholder {
    color: #949494;
  }

</style>

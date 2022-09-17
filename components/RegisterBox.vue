<template>
  <div class="d-flex flex-column">
    <div class="d-flex flex-row justify-content-between">
      <div></div>
      <p>아직 회원이 아니신가요?</p>
      <div></div>
    </div>
    <div class="d-flex flex-column">
      <NuxtLink to="/register">
        <button class="neoguri-btn-style-2 w-100 py-3">회원가입</button>
      </NuxtLink>
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

</style>

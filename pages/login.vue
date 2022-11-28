<template>
  <div class="d-flex flex-column">
    <header-box title="로그인" />

    <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">
      <neoguri-password-banner />
      <div class="d-flex flex-column text-center">
        <p class="neoguri-font-weight-400 fs-6 mb-0"><span class="font-weight-bold">암호</span>를 입력해주세요.</p>
      </div>

      <div class="pt-4">
        <neoguri-input
          name="password"
          v-model="password"
          placeholder="암호"
          :input="onPasswordChanged"
        />
      </div>

      <div class="d-flex flex-column mb-4">
        <neoguri-button
          type="primary"
          @click.native=""
        >
          <template v-slot:content>계속하기</template>
        </neoguri-button>
      </div>

      <neoguri-horizontal-titled-divider>
        <template v-slot:title>
          <NuxtLink to="" class="d-flex px-3 text color-neoguri-gray text-underline"><span class="font-weight-bold line">암호</span>를 잊으셨나요?</NuxtLink>
        </template>
      </neoguri-horizontal-titled-divider>


<!--      <div class="pt-4">-->
<!--        <sns-login-box />-->
<!--      </div>-->

    </div>

    <footer-box />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import HeaderBox from '~/components/common/HeaderBox.vue';
import FooterBox from "~/components/common/FooterBox.vue";
import LoginBox from '@/components/LoginBox.vue';
import RegisterBox from '@/components/RegisterBox.vue';
import SnsLoginBox from '@/components/SnsLoginBox.vue';
import NeoguriPasswordBanner from '~/components/common/banners/NeoguriPasswordBanner.vue';
import NeoguriInput from "~/components/common/inputs/texts/NeoguriInput.vue";
import NeoguriButton from "~/components/common/inputs/buttons/NeoguriButton.vue";
import NeoguriHorizontalTitledDivider from "~/components/common/NeoguriHorizontalTitledDivider.vue";

export default Vue.extend({
  name: 'LoginPage',
  components: {
    'header-box': HeaderBox,
    'footer-box': FooterBox,
    'login-box': LoginBox,
    'register-box': RegisterBox,
    'sns-login-box': SnsLoginBox,
    'neoguri-input': NeoguriInput,
    'neoguri-button': NeoguriButton,
    'neoguri-password-banner': NeoguriPasswordBanner,
    'neoguri-horizontal-titled-divider': NeoguriHorizontalTitledDivider
  },
  data () {
    return {
      password: '',
    };
  },
  methods: {
    onPasswordChanged () {
    }
  }
})
</script>

<style scoped>
</style>

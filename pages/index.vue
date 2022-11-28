<template>
  <div class="d-flex flex-column">
    <header-box title="로그인" />

    <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">
      <neoguri-intro-banner />

      <div class="d-flex flex-column text-center">
        <h2 class="neoguri-font-weight-700 color-neoguri-title pb-4 mb-0">너구리소굴</h2>
        <p class="neoguri-font-weight-400 fs-6 mb-0">너구리소굴에 방문하신 것을 진심으로 환영합니다.</p>
      </div>

      <div class="pt-4">
        <neoguri-input
          v-model="email"
          placeholder="이메일"
          @input.native="() => {

          }"
        />
      </div>

      <div class="login-buttons d-flex flex-column">
        <neoguri-button
          type="primary"
          @click.native="submit"
        >
          <template v-slot:content>계속하기</template>
        </neoguri-button>
      </div>
    </div>
    <footer-box />
  </div>
</template>


<script lang="ts">
import Vue from 'vue'
import NeoguriIntroBanner from "~/components/common/banners/NeoguriIntroBanner.vue";
import HeaderBox from "~/components/common/HeaderBox.vue";
import FooterBox from "~/components/common/FooterBox.vue";
import NeoguriInput from "~/components/common/inputs/texts/NeoguriInput.vue";
import NeoguriButton from "~/components/common/inputs/buttons/NeoguriButton.vue";


export default Vue.extend({
  name: 'IndexPage',
  components: {
    'header-box': HeaderBox,
    'neoguri-intro-banner': NeoguriIntroBanner,
    'neoguri-input': NeoguriInput,
    'neoguri-button': NeoguriButton,
    'footer-box': FooterBox
  },
  data () {
    return {
      email: ''
    };
  },
  methods: {
    validateEmail() {

    },

    submit() {
      (this.$data.email.length > 0)
        ? this.$router.push('/login')
        : this.$router.push('/register');

    }
  }

})
</script>

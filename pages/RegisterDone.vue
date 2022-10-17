<template>
  <div class="d-flex flex-column">
    <template v-if="this.level == 1">

      <HeaderBox title="너구리단 가입" />

      <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">

        <div class="pt-2">
          <LoginIdInput name="login_id" title="아이디" v-model="loginId" confirm-button-title="중복확인" required />
        </div>

        <div class="pt-2">
          <PasswordInput name="password" title="비밀번호" v-model="password" required />
        </div>

        <div class="pt-2">
          <PasswordConfirmInput name="password_confirm" title="비밀번호 확인" required v-model="passwordConfirm" :password="password.value" />
        </div>

        <div class="pt-2">
          <EmailInput name="email" title="이메일" confirm-button-title="중복확인" v-model="email" required />
        </div>

        <div v-if="this.isInvalid" class="pt-3">
          <template v-for="description in this.invalidInputDescriptions">
            <p class="pt-2">{{ description }}</p>
          </template>
        </div>
        <div class="d-flex pt-3 flex-column">
          <button class="neoguri-btn-style-1 py-3 border-0" @click="submitLevel1">너구리단 가입하기</button>
        </div>
      </div>
    </template>
    <template v-if="this.level == 2">
      <HeaderBox title="너구리 등록증 발급" />

      <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">

        <div class="pt-2">
          <NicknameInput name="nickname" title="닉네임" v-model="nickname" confirm-button-title="중복확인" required />
        </div>
        <div class="pt-2">
          <AgeBandSelect name="age" title="연령대" v-model="age" required />
        </div>
        <div class="pt-2">
          <GenderRadioGroup name="gender" title="성별" v-model="gender" :items="this.genderRadioGroup" required />
        </div>
        <div class="pt-2">
          <DateInput name="birthdate" title="생일" v-model="birthdate" required />
        </div>

        <div v-if="this.isInvalid" class="pt-3">
          <template v-for="description in this.invalidInputDescriptions">
            <p class="pt-2">{{ description }}</p>
          </template>
        </div>
        <div class="d-flex pt-3 flex-column">
          <button class="neoguri-btn-style-1 py-3 border-0" :disabled="this.isInvalid ? 'true' : null" @click="submit">너구리단 가입하기</button>
        </div>
      </div>
    </template>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HeaderBox from '@/components/common/HeaderBox.vue'
import LoginIdInput from '~/components/common/inputs/LoginIdInput.vue'
import PasswordInput from '~/components/common/inputs/PasswordInput.vue'
import PasswordConfirmInput from '~/components/common/inputs/PasswordConfirmInput.vue'
import EmailInput from '~/components/common/inputs/EmailInput.vue'
import NicknameInput from '~/components/common/inputs/NicknameInput.vue'
import AgeBandSelect from '~/components/common/inputs/AgeBandSelect.vue'
import GenderRadioGroup from "~/components/common/inputs/radios/GenderRadioGroup.vue";
import DateInput from "~/components/common/inputs/DateInput.vue";

export default Vue.extend({
  name: 'RegisterPage',
  components: {
    HeaderBox,
    LoginIdInput,
    PasswordInput,
    PasswordConfirmInput,
    EmailInput,
    NicknameInput,
    AgeBandSelect,
    GenderRadioGroup,
    DateInput,
  },
  data() {
    return {
      level: 1,

      loginId: { value: '', isValid: false },
      password: { value: '', isValid: false },
      passwordConfirm: { value: '', isValid: false },
      email: { value: '', isValid: false },

      nickname: { value: '', isValid: false },
      age: { value: '', isValid: false },

      gender: { value: '', isValid: false },
      genderRadioGroup: [
        { value: 'M', title: '남성' },
        { value: 'F', title: '여성' },
      ],

      birthdate: { value: '', isValid: false },

      loginIdDuplicateCheck: false,
      emailDuplicateCheck: false,
      serviceAgreementCheck: false,
      invalidInputDescriptions: [],
    }
  },
  computed: {
    isInvalid(): boolean {
      return this.$data.invalidInputDescriptions.length > 0
        || !this.$data.loginId.isValid
        || !this.$data.password.isValid
        || !this.$data.passwordConfirm.isValid
        || !this.$data.email.isValid
    }
  },
  watch: {
  },
  methods: {
    submitLevel1() {
      const loginId = this.$data.loginId;
      const password = this.$data.password;
      const email = this.$data.email;

      const payload = {
        loginId: loginId.value,
        password: password.value,
        email: email.value,
      }
      console.log('submit register with payload:', payload);

      this.$data.level = 2;
    }
  }
})
</script>

<style scoped>
</style>

<template>
  <div class="d-flex flex-column">
    <header-box :title="titles[level - 1]" />

    <div class="neoguri-container d-flex flex-column p-3 container-sm pb-5 bg-neoguri-lightgray">
      <!-- Progress bar -->
      <div class="d-flex w-100 position-relative justify-content-center align-items-center">

        <!-- prev button -->
        <button class="left border-0 bg-transparent p-0 position-absolute" v-if="hasPrev" @click="goPrev">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="14" cy="14" r="14" fill="#FAFAFA"/>
            <rect x="1.1665" y="2.33398" width="23.3333" height="23.3333" fill="white" fill-opacity="0.01"/>
            <path d="M15.5486 6.50741C15.9283 6.12774 16.5438 6.12774 16.9235 6.50741C17.274 6.85788 17.301 7.40936 17.0044 7.79075L16.9235 7.88234L10.3201 14.4865L16.9235 21.0907C17.274 21.4412 17.301 21.9927 17.0044 22.3741L16.9235 22.4657C16.5731 22.8161 16.0216 22.8431 15.6402 22.5466L15.5486 22.4657L8.25693 15.174C7.90645 14.8235 7.8795 14.2721 8.17605 13.8907L8.25693 13.7991L15.5486 6.50741Z" fill="#BDBDBD"/>
          </svg>
        </button>
        <!-- prev button -->

        <!-- progress -->
        <div class="d-flex w-50 align-items-center position-relative">
          <div class="divider d-flex w-100 position-absolute"></div>
          <div class="progress-items d-flex w-100 align-items-center justify-content-between">
            <template v-for="item in [0, 1, 2]">
              <!-- 완료 -->
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg" v-if="item < level">
                <circle cx="10" cy="10" r="10" fill="#DC6800"/>
                <path d="M4 10.3829L8.10933 14.5L16 6.61717L14.8672 5.5L8.10933 12.25L5.11715 9.25784L4 10.3829Z" fill="white"/>
              </svg>
              <!-- 완료 -->

              <!-- 진행중 -->
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg" v-else-if="item === level">
                <circle cx="10" cy="10" r="10" fill="#DC6800"/>
                <circle cx="10" cy="10" r="3.75" fill="white"/>
              </svg>
              <!-- 진행중 -->

              <!-- 미진행 -->
              <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg" v-else>
                <path d="M19.3413 10C19.3413 15.2505 15.1198 19.5 9.92064 19.5C4.72151 19.5 0.5 15.2505 0.5 10C0.5 4.74953 4.72151 0.5 9.92064 0.5C15.1198 0.5 19.3413 4.74953 19.3413 10Z" fill="white" stroke="#B7B7B7"/>
              </svg>
              <!-- 미진행 -->

            </template>
          </div>
        </div>

        <!-- next button -->
        <button class="right border-0 bg-transparent p-0 position-absolute" v-if="hasNext" @click="goNext">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="14" cy="14" r="14" transform="rotate(180 14 14)" fill="#FAFAFA"/>
            <rect x="26.8335" y="25.666" width="23.3333" height="23.3333" transform="rotate(180 26.8335 25.666)" fill="white" fill-opacity="0.01"/>
            <path d="M12.4514 21.4926C12.0717 21.8723 11.4562 21.8723 11.0765 21.4926C10.726 21.1421 10.699 20.5906 10.9956 20.2092L11.0765 20.1177L17.6799 13.5135L11.0765 6.90925C10.726 6.55878 10.699 6.00731 10.9956 5.62591L11.0765 5.53432C11.4269 5.18385 11.9784 5.15689 12.3598 5.45345L12.4514 5.53432L19.7431 12.826C20.0935 13.1765 20.1205 13.7279 19.824 14.1093L19.7431 14.2009L12.4514 21.4926Z" fill="#BDBDBD"/>
          </svg>
        </button>
        <!-- next button -->
      </div>
    </div>

    <div class="neoguri-container d-flex flex-column px-3 container-sm pb-5">
      <template v-if="level === 1">
        <!-- 너구리단 가입 -->
        <div class="pt-4">
          <neoguri-input
            name="password"
            v-model="password"
            placeholder="암호"
            :input="() => {

            }"
          >
            <template v-slot:title>
              암호<span class="mb-0 ml-1 color-neoguri-red">*</span>
            </template>

            <div class="d-flex">
              <span v-if="passwordValidation" class="color-neoguri-valid">
                사용 가능한 암호입니다.
              </span>
              <span v-if="!passwordValidation" class="color-neoguri-invalid">
                6자 이상 20자 이하로 입력해주세요.
              </span>
            </div>
          </neoguri-input>
        </div>

        <div class="pt-4">
          <div class="mb-2 d-flex">
            <span class="neoguri-font-weight-500 mb-0">
              약관 동의<span class="mb-0 ml-1 color-neoguri-red">*</span>
            </span>
          </div>
          <neoguri-agreement-checkbox
            title="서비스 이용 약관에 동의합니다."
            v-model="agreementChecked"
            :callback="openAgreementDetailModal"
          >

          </neoguri-agreement-checkbox>
        </div>
        <div class="d-flex mt-4 flex-column">
          <button class="neoguri-btn-style-1 py-3 border-0" :disabled="!(passwordValidation && agreementChecked)" @click="submitFirst">너구리단 가입하기</button>
        </div>
        <!-- 너구리단 가입 -->
      </template>
      <template v-if="level === 2">
        <!-- 너굴 등록증 발급 -->
        <div class="pt-4">
          <neoguri-input
            name="password"
            v-model="password"
            placeholder="암호"
            :input="() => {

            }"
          >
            <template v-slot:title>
              암호<span class="mb-0 ml-1 color-neoguri-red">*</span>
            </template>

            <div class="d-flex">
              <span v-if="passwordValidation" class="color-neoguri-valid">
                사용 가능한 암호입니다.
              </span>
              <span v-if="!passwordValidation" class="color-neoguri-invalid">
                6자 이상 20자 이하로 입력해주세요.
              </span>
            </div>
          </neoguri-input>
        </div>
        <div class="pt-4">
          <neoguri-date-picker
            name="birthdate"
            v-model="birthdate"
            placeholder="YYYY.MM.DD"
            :input="() => {

            }"
          >
            <template v-slot:title>
              생일<span class="mb-0 ml-1 color-neoguri-red">*</span>
            </template>

            <div class="d-flex">
              <span v-if="passwordValidation" class="color-neoguri-valid">
                사용 가능한 암호입니다.
              </span>
              <span v-if="!passwordValidation" class="color-neoguri-invalid">
                6자 이상 20자 이하로 입력해주세요.
              </span>
            </div>
          </neoguri-date-picker>
        </div>
        <div class="pt-4">
          <neoguri-address-input
            name="birthdate"
            v-model="address"
            placeholder="YYYY.MM.DD"
            :input="() => {

            }"
          >
            <template v-slot:title>
              주소<span class="mb-0 ml-1 color-neoguri-red">*</span>
            </template>

          </neoguri-address-input>
        </div>
        <div class="pt-4">
          <neoguri-radio-group
            name="gender"
            v-model="gender"
            :items="[
              { title: '여성', value: 'F' },
              { title: '남성', value: 'M' },
              { title: '미응답', value: 'X', isDefault: true },
            ]"
            :input="() => {

            }"
          >
            <template v-slot:title>
              성별
            </template>

            <div class="d-flex">
              <span v-if="passwordValidation" class="color-neoguri-valid">
                사용 가능한 암호입니다.
              </span>
              <span v-if="!passwordValidation" class="color-neoguri-invalid">
                6자 이상 20자 이하로 입력해주세요.
              </span>
            </div>
          </neoguri-radio-group>
        </div>

        <div class="d-flex mt-4 flex-column">
          <button class="neoguri-btn-style-1 py-3 border-0" @click="submitFinal">너구리단 가입하기</button>
        </div>
        <!-- 너굴 등록증 발급 -->
      </template>
    </div>
    <service-term-modal ref="serviceTermModal" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HeaderBox from '@/components/common/HeaderBox.vue'
import NeoguriInput from "@/components/common/inputs/texts/NeoguriInput.vue";
import NeoguriAgreementCheckbox from "@/components/common/inputs/checkboxes/NeoguriAgreementCheckbox.vue";
import NeoguriDatePicker from "~/components/common/inputs/pickers/NeoguriDatePicker.vue";
import NeoguriRadioGroup from "~/components/common/inputs/checkboxes/NeoguriRadioGroup.vue";
import NeoguriAddressInput from "~/components/common/inputs/texts/NeoguriAddressInput.vue";
import ServiceTermModal from "~/components/common/modals/ServiceTermModal.vue";

export default Vue.extend({
  name: 'RegisterPage',
  head () {
    return {
      script: [
        { hid: 'script', src: 'https://t1.daumcdn.net/mapjsapi/bundle/postcode/prod/postcode.v2.js', defer: true },
      ]
    }
  },
  components: {
    'header-box': HeaderBox,
    'neoguri-input': NeoguriInput,
    'neoguri-address-input': NeoguriAddressInput,
    'neoguri-date-picker': NeoguriDatePicker,
    'neoguri-radio-group': NeoguriRadioGroup,
    'neoguri-agreement-checkbox': NeoguriAgreementCheckbox,
    'service-term-modal': ServiceTermModal
  },
  props: {
    titles: {
      type: Array,
      default: () => {
        return ['너구리단 가입', '너굴 등록증 발급'];
      }
    },

  },
  data() {
    return {
      level: 1,
      maxAttachedLevel: 1,

      password: '',
      agreementChecked: false,

      nickname: '',
      birthdate: '',
      address: {
        address: '',
        addressDetail: ''
      },
      gender: '',

    }
  },
  computed: {
    title() {
      const title: string = this.$props.titles[this.$data.level - 1];
      console.log(this.$props.titles, title);
      return title;
    },
    hasPrev() {
      const currentLevel: number = this.$data.level;

      return (1 < currentLevel);
    },
    hasNext() {
      const maxAttachedLevel: number = this.$data.maxAttachedLevel;
      const currentLevel: number = this.$data.level;

      return (maxAttachedLevel > currentLevel);
    },

    passwordValidation() {
      const _data = this.$data;
      const password: string = _data.password;

      return (password.length > 0);
    },

  },
  watch: {
  },
  methods: {
    goPrev() {
      let level = this.$data.level;
      if (level === 1) {
        return;
      }

      this.$data.level = level - 1;
    },
    goNext() {

      let level = this.$data.level;
      if (level === 2) {
        return;
      }

      this.$data.level = level + 1;
      if (this.$data.maxAttachedLevel !== this.level) {
        this.$data.maxAttachedLevel = this.$data.level;
      }
    },
    openAgreementDetailModal() {
      console.log('open');
      const _refs = this.$refs;
      if (_refs.serviceTermModal) {
        _refs.serviceTermModal.openModal();
      }
    },

    submitFirst() {
      this.goNext();
    },

    submitFinal() {
      this.$router.push('/profile');
    }

  }
})
</script>

<style scoped>

  .btn-progress {
    width: 28px;
    height: 28px;
  }

  .divider {
    height: 2px;
    background-color: #979797;
  }

  .progress-items {
    z-index: 1;
  }
</style>

<script lang="ts">
import AbstractConfirmInput from "~/components/common/inputs/AbstractConfirmInput.vue";

export default AbstractConfirmInput.extend({
  name: 'NicknameInput',
  props: {
    validDescription: {
      type: String,
      default: '사용 가능한 닉네임입니다.'
    },
    invalidDescription: {
      type: String,
      default: '닉네임은 한글,영문,숫자만 가능하며 2자 ~ 10자 이내로 작성해주세요'
    },
    confirmDescription: {
      type: String,
      default: '중복확인을 진행해주세요'
    },

  },
  methods: {
    confirm() {
      // TODO: 중복체크
      this.isConfirmed = true;
    },
    validate(): boolean {
      return /^[ㄱ-ㅎ가-힣a-zA-Z\d]{2,10}$/.test(this.$data.value)
    }
  }
})

</script>

<script lang="ts">
import AbstractConfirmInput from "~/components/common/inputs/AbstractConfirmInput.vue";

export default AbstractConfirmInput.extend({
  name: 'LoginIdInput',
  props: {
    validDescription: {
      type: String,
      default: '사용 가능한 아이디입니다.'
    },
    invalidDescription: {
      type: String,
      default: '아이디는 영문, 숫자 조합으로 5자 ~ 15자 이내로 작성해주세요'
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
      return /^[a-zA-Z\d]{5,15}$/.test(this.$data.value)
    }
  }
})

</script>

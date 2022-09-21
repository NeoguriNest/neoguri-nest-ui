<script lang="ts">
import AbstractConfirmInput from "~/components/common/inputs/AbstractConfirmInput.vue";

export default AbstractConfirmInput.extend({
  name: 'EmailInput',
  props: {
    validDescription: {
      type: String,
      default: '사용할 수 있는 이메일입니다.'
    },
    invalidDescription: {
      type: String,
      default: '알맞지 않은 형식입니다. (.co.kr, .com 도메인만 지원)'
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
      return /^[a-zA-Z0-9]+@[a-zA-Z0-9]+.co(m|.kr)$/.test(this.$data.value)
    }
  }
})

</script>

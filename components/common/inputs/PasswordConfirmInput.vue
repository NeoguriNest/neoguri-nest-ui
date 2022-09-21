<script lang="ts">
import AbstractPasswordInput from "~/components/common/inputs/AbstractPasswordInput.vue";

export default AbstractPasswordInput.extend({
  name: 'PasswordInput',
  props: {
    validDescription: {
      type: String,
      default: '입력하신 비밀번호가 일치합니다.'
    },
    invalidDescription: {
      type: String,
      default: '입력하신 비밀번호가 불일치합니다.'
    },
    password: {
      type: String,
      required: true
    }
  },
  methods: {
    validate(): boolean {
      return this.$data.value === this.password
    }
  }
})
</script>

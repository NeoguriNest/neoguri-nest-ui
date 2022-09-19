<script lang="ts">
import AbstractPasswordInput from "~/components/common/inputs/AbstractPasswordInput.vue";

export default AbstractPasswordInput.extend({
  name: 'PasswordInput',
  methods: {
    validate(): boolean {
      return /^(?=.*[A-Za-z])(?=.*\d)(?=.*[$@$!%*#?&])[A-Za-z\d$@$!%*#?&]{6,12}$/.test(this.$data.value)
    }
  }
})
</script>

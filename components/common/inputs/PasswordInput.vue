<script lang="ts">
import AbstractInput from "~/components/common/inputs/AbstractInput.vue";
import { Component } from "nuxt-property-decorator";

@Component
export default class PasswordInput extends AbstractInput {

  validate(): boolean {
    return /^(?=.*[A-Za-z])(?=.*\d)(?=.*[$@$!%*#?&])[A-Za-z\d$@$!%*#?&]{6,12}$/.test(this.value)
  }

}
</script>

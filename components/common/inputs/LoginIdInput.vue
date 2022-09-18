<script lang="ts">
import AbstractInput from "~/components/common/inputs/AbstractInput.vue";
import { Component } from "nuxt-property-decorator";

@Component
export default class LoginIdInput extends AbstractInput {

  validate(): boolean {
    console.log('login input', /^[a-zA-Z\d]{5,}$/.test(this.value))
    return /^[a-zA-Z\d]{5,}$/.test(this.value)
  }

}
</script>

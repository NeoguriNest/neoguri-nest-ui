<script lang="ts">
import AbstractInput from "~/components/common/inputs/AbstractInput.vue";
import { Component } from "nuxt-property-decorator";

@Component
export default class EmailInput extends AbstractInput {

  validate(): boolean {
    return /^[a-zA-Z0-9]+@[a-zA-Z0-9]+$/.test(this.value)
  }

}
</script>

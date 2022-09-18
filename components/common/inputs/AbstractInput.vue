<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">{{ this.title }}</span>
        <span v-if="this.required" class="mb-0 ml-1 color-neoguri-red">*</span>
      </div>
      <input type="text" :placeholder="this.getPlaceholder()" :name="this.name" :value="this.value" @input="this.updateValue" class="py-3 px-4 mb-2" />
    </div>
    <div class="d-flex">
      <span v-if="(this.value.length && this.isValid)" class="color-neoguri-valid">VALID {{ this.validDescription }}</span>
      <span v-if="(this.value.length && !this.isValid)" class="color-neoguri-invalid">INVALID {{ this.invalidDescription }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { Prop, Watch } from "nuxt-property-decorator";
import Vue, { watch } from "vue";

export default abstract class AbstractInput extends Vue {

  @Prop({ type: String })
  name!: string

  @Prop({ type: String })
  title!: string

  @Prop({ type: Boolean, required: false, default: false })
  required?: boolean

  @Prop({ type: String, required: false })
  placeholder?: string

  @Prop({ type: String, required: false })
  validDescription?: string

  @Prop({ type: String, required: false })
  invalidDescription?: string

  value: string = ''

  isValid: boolean = false

  abstract validate(): boolean

  /**
   * prefix 'get' or 'is' mean it is computed value
   */
  getPlaceholder(): string {
    return this.placeholder === undefined ? this.title : this.placeholder
  }
  /** End computed declare */

  updateValue = ($event: { target: { value: string }}) => {
    this.value = $event.target.value
    this.isValid = this.validate()
  }
}
</script>

<style scoped>
  input[type=text] {
    border: 1px solid #DFDFDF;
  }

  input::placeholder {
    color: #949494;
  }

</style>

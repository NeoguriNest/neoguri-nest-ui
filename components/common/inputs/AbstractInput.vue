<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">{{ this.title }}</span>
        <span v-if="this.required" class="mb-0 ml-1 color-neoguri-red">*</span>
      </div>
      <input :type="this.type" :placeholder="this.computedPlaceholder" v-model="value" class="py-3 px-4"/>
    </div>
    <div class="d-flex">
      <span v-if="this.value.length && this.validate()" class="color-neoguri-valid">
        {{ this.validDescription }}
      </span>
      <span v-if="this.value.length && !this.validate()" class="color-neoguri-invalid">
        {{ this.invalidDescription }}
      </span>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend(
  {
  name: 'AbstractInput',
  props: {
    name: {
      type: String,
    },
    title: {
      type: String,
    },
    type: {
      type: String,
      required: true,
      default: 'text'
    },
    required: {
      type: Boolean,
      required: false,
      default: false
    },
    placeholder: {
      type: String,
      required: false
    },
    validDescription: {
      type: String,
      required: false
    },
    invalidDescription: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      value: ''
    }
  },
  computed: {
    computedPlaceholder() {
      return (this && this.placeholder)
        ? this.placeholder
        : this.title
    },
  },
  methods: {
    validate(): boolean {
      // TODO: override
      throw new Error('Method must be implemented. name: \'validate\'')
    }
  },
  watch: {
    value(newValue: string, oldValue: string) {
      this.$emit('input', newValue)
    }
  }
})
</script>

<style scoped>
input {
  border: 1px solid #DFDFDF;
}

input::placeholder {
  color: #949494;
}

</style>

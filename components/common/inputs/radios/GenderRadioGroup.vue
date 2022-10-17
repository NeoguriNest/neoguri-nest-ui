<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">{{ this.title }}</span>
        <span v-if="this.required" class="mb-0 ml-1 color-neoguri-red">*</span>
      </div>

      <div class="flex-column">
        <label class="mr-4" v-for="item in this.items">
          <input type="radio" :name="name" :value="item.value" v-model="value">
          {{ item.title }}
        </label>
      </div>

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

import AbstractRadioGroup from "~/components/common/inputs/radios/AbstractRadioGroup.vue";

export default AbstractRadioGroup.extend(
  {
  name: 'GenderRadioGroup',
  props: {
    name: {
      type: String,
    },
    title: {
      type: String,
    },
    required: {
      type: Boolean,
      required: false,
      default: false
    },

    /**
     * @requires items: [{value: String, title: String}, ...]
     */
    items: {
      type: Array,
      required: true
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
  },
  methods: {
    validate(): boolean {
      return this.$data.value !== ''
    }
  },
  watch: {
    value(newValue: string, oldValue: string) {
      this.$emit('input', { value: newValue, isValid: this.validate() } )
    }
  }
})
</script>

<style scoped>
select {
  border: 1px solid #DFDFDF;
}

select::placeholder {
  color: #949494;
}

</style>

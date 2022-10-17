<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">{{ this.title }}</span>
        <span v-if="this.required" class="mb-0 ml-1 color-neoguri-red">*</span>
      </div>

      <div class="flex-column">
        <label v-for="item in this.items">
          <input type="radio" :name="this.name" :value="item.value" v-model="value">
          <p>{{ item.text }}</p>
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
import Vue from "vue";

export default Vue.extend(
  {
  name: 'AbstractSelect',
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
      // TODO: override
      throw new Error('Method must be implemented. name: \'validate\'')
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

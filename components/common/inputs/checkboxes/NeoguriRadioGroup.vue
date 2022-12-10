<template>
  <div class="d-flex flex-column">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">
          <slot name="title"></slot>
        </span>
      </div>

      <div class="d-flex flex-row">
        <label v-for="item in items" class="d-flex flex-row justify-content-center align-items-center mb-0 py-1" :active="value === item.value">
          <input type="radio" :name="name" :value="item.value" v-model="value" :checked="item.isDefault">
          <p class="mb-0">{{ item.title }}</p>
        </label>

      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend(
  {
  name: 'NeoguriRadioGroup',
  props: {
    name: {
      type: String,
    },
    title: {
      type: String,
    },
    /**
     * @requires items: [{value: String, title: String, isDefault?: boolean}, ...]
     */
    items: {
      type: Array,
      required: true
    },
  },
  data() {
    return {
      value: ''
    }
  },
  computed: {
  },
  methods: {
  },
  watch: {
    value(value: string) {
      this.$emit('input', value)
    }
  }
})
</script>

<style scoped>
  label {
    min-width: 80px;
    margin-left: 10px;
    border: 1px solid #DFDFDF;
    background-color: #FFFFFF;
  }

  label:first-child {
    margin-left: 0;
  }

  label[active=true] {
    color: #FFFFFF;
    border: none;
    background-color: #E58E40;
  }

  input[type=radio] {
    display: none;
  }

</style>

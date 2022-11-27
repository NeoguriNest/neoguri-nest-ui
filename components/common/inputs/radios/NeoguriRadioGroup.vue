<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">
          <slot name="title"></slot>
        </span>
      </div>

      <div class="flex-column">
        <label v-for="item in this.items">
          <input type="radio" :name="this.name" :value="item.value" v-model="value">
          <p>{{ item.text }}</p>
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
     * @requires items: [{value: String, title: String}, ...]
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
select {
  border: 1px solid #DFDFDF;
}

select::placeholder {
  color: #949494;
}

</style>

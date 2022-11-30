<template>
  <div class="d-flex flex-column">
    <div class="input-group flex-column mb-1">
      <div class="d-flex flex-row align-items-center">
        <label class="d-flex flex-row align-items-center mb-0">
          <input type="checkbox" :name="this.name" v-model="value">
          <p class="my-0 mx-0 ml-2 align-middle">{{ title }}</p>
        </label>

        <button
          class="ml-3 py-1 px-3 border-0 rounded-sm" @click="callback">
          약관보기
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend(
  {
  name: 'NeoguriAgreementCheckbox',
  props: {
    name: {
      type: String,
    },
    title: {
      type: String,
    },

    callback: {
      type: Function,
      default: () => {}
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

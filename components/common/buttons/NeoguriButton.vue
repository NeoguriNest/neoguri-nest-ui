<template>
  <button type="button" :class="((type) ? types[type] + ' ' : '') + 'py-3 border-0'">
    <slot name="content"></slot>
  </button>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend(
  {
    name: 'NeoguriButton',
    props: {
      type: {
        type: String,
        required: true
      },
      types: {
        type: Object,
        default: () => {
          return {
            'primary': 'neoguri-btn-style-1',
            'secondary': 'neoguri-btn-style-2'
          };
        },
      }
    },
    data () {
      return {
        value: '',
        isConfirmed: false
      }
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

  input {
   border: 1px solid #DFDFDF;
  }

  input::placeholder {
    color: #949494;
  }

</style>

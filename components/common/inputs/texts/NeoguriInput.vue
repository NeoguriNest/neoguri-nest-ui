<template>
  <div class="d-flex flex-column">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">
          <slot name="title"></slot>
        </span>
      </div>
      <input :type="this.type" :name="name" :placeholder="this.placeholder" v-model="value" class="py-3 px-4"/>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend(
  {
    name: 'NeoguriInput',
    props: {
      type: {
        type: String,
        default: 'text'
      },
      name: {
        type: String,
      },
      placeholder: {
        type: String,
        default: '내용을 입력해주세요'
      },
    },
    data() {
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

<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">{{ this.title }}</span>
        <span v-if="this.required" class="mb-0 ml-1 color-neoguri-red">*</span>
      </div>
      <div class="d-flex justify-content-between">
        <input :type="this.type" :placeholder="this.computedPlaceholder" v-model="value" class="w-75 py-3 px-4 mr-2"/>
        <button class="neoguri-btn-lightgray  w-25 py-3 border-0" @click="this.confirm">{{ this.confirmButtonTitle }}</button>
      </div>
    </div>
    <div class="d-flex">
      <template v-if="this.value.length">
        <span v-if="!this.isConfirmed" class="color-neoguri-invalid">
          {{ this.confirmDescription }}
        </span>
        <template v-else>
          <span v-if="this.validate()" class="color-neoguri-valid">
            {{ this.validDescription }}
          </span>
          <span v-if="!this.validate()" class="color-neoguri-invalid">
            {{ this.invalidDescription }}
          </span>
        </template>
      </template>
    </div>
  </div>
</template>

<script lang="ts">
import AbstractInput from "~/components/common/inputs/AbstractInput.vue";

export default AbstractInput.extend(
  {
    name: 'AbstractConfirmInput',
    props: {
      type: {
        type: String,
        default: 'text'
      },
      confirmDescription: {
        type: String,
        default: '중복확인을 진행해주세요'
      },
      confirmButtonTitle: {
        type: String,
        required: true
      }
    },
    data() {
      return {
        isConfirmed: false
      }
    },
    methods: {
      confirm() {
        throw new Error('Method must be implemented. name: \'confirm\'')
      }
    },
    watch: {
      value(newValue: string, oldValue: string) {
        this.$emit('input', { value: newValue, isValid: this.validate() } )

        if (newValue !== oldValue) {
          this.isConfirmed = false
        }
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

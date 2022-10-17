<script lang="ts">

import AbstractTextInput from "~/components/common/inputs/AbstractTextInput.vue";

export default AbstractTextInput.extend(
  {
    name: 'AddressInput',
    props: {
      type: {
        type: String,
        default: 'text'
      }
    },
    methods: {
      validate(): boolean {
        return this.$data.value !== ''
      }
    }
  })
</script>

<script lang="ts">

import AbstractTextInput from "~/components/common/inputs/AbstractTextInput.vue";

export default AbstractTextInput.extend(
  {
    name: 'DateInput',
    props: {
      type: {
        type: String,
        default: 'date'
      }
    },
    methods: {
      validate(): boolean {
        return this.$data.value !== ''
      }
    }
  })
</script>

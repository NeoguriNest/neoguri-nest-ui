<script lang="ts">
import AbstractTextInput from "~/components/common/inputs/AbstractTextInput.vue";

export default AbstractTextInput.extend({
  name: 'EmailInput',
  methods: {
    validate(): boolean {
      return /^[a-zA-Z0-9]+@[a-zA-Z0-9]+$/.test(this.$data.value)
    }
  }
})

</script>

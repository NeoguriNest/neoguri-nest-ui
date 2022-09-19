<script lang="ts">
import AbstractTextInput from "~/components/common/inputs/AbstractTextInput.vue";

export default AbstractTextInput.extend({
  name: 'LoginIdInput',
  methods: {
    validate(): boolean {
      return /^[a-zA-Z\d]{5,}$/.test(this.$data.value)
    }
  }
})

</script>

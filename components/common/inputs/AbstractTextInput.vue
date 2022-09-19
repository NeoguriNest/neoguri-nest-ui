<script lang="ts">
import AbstractInput from "~/components/common/inputs/AbstractInput.vue";

export default AbstractInput.extend(
  {
    name: 'AbstractTextInput',
    props: {
      type: {
        type: String,
        default: 'text'
      }
    }
  })
</script>

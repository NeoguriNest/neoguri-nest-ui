<script lang="ts">
import AbstractInput from "~/components/common/inputs/AbstractInput.vue";

export default AbstractInput.extend(
  {
    name: 'AbstractPasswordInput',
    props: {
      type: {
        type: String,
        default: 'password'
      }
    }
  })
</script>

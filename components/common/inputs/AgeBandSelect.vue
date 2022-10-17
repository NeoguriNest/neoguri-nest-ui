<script lang="ts">

import AbstractSelect from "~/components/common/inputs/AbstractSelect.vue";

export default AbstractSelect.extend(
  {
  name: 'AgeBandSelect',
  props: {
    /**
     * @requires options: [{value: String, title: String}, ...]
     */
    options: {
      type: Array,
      required: true,
      default: [
        { value: '0', title: '연령대를 선택해주세요' },
        { value: '10', title: '10대' },
        { value: '20', title: '20대' },
        { value: '30', title: '30대' },
        { value: '40', title: '40대' },
        { value: '50', title: '50대' },
      ]
    },
  },
  data() {
    return {
      value: ''
    }
  },
  computed: {
  },
  methods: {
    validate(): boolean {
      return this.$data.value !== ''
    }
  },
  watch: {
    value(newValue: string, oldValue: string) {
      this.$emit('input', { value: newValue, isValid: this.validate() } )
    }
  }
})
</script>

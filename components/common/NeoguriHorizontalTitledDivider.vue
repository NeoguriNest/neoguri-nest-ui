<template>
  <div class="d-flex flex-row justify-content-center align-items-center position-relative">
    <div class="divider-background-line d-flex w-100 position-absolute"></div>
    <div class="d-flex text-center bg-white">
      <slot name="title"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "NeoguriHorizontalTitledDivider"
}
</script>

<style scoped>
  .divider-background-line {
    border-bottom: 1px solid #DFDFDF;
    z-index: -1;
  }

</style>

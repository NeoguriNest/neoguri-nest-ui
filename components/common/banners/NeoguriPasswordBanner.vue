<template>
  <div class="d-flex w-100 py-4 justify-content-center">
    <img class="neoguri-banner w-100 h-100" src="/img/password-banner.png" alt="암호를대라 배너"/>
  </div>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  name: 'NeoguriPasswordBanner'
});

</script>
<style>
.neoguri-banner {
  max-width: 340px;
}
</style>

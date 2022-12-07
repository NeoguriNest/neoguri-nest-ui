<template>
  <div class="neoguri-modal d-flex justify-content-center align-items-center" v-if="status === 1">
    <div class="neoguri-modal-content d-flex flex-column overflow-hidden rounded-sm">
      <div class="w-100 py-2 px-3 d-flex flex-row justify-content-between neoguri-font-weight-500 bg-neoguri-orange">
        <h5 class="d-flex align-items-center text-white mb-0">서비스 이용약관</h5>
        <button class="d-flex px-0 border-0 bg-transparent" @click="closeModal">
          <svg width="30" height="30" viewBox="0 0 30 30" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="30" height="30" fill="white" fill-opacity="0.01"/>
            <path d="M14.9998 14.0356L20.6541 8.38134C20.9203 8.11507 21.352 8.11507 21.6183 8.38134C21.8846 8.64761 21.8846 9.07931 21.6183 9.34558L15.9641 14.9998L21.6183 20.6541C21.8846 20.9203 21.8846 21.352 21.6183 21.6183C21.352 21.8846 20.9203 21.8846 20.6541 21.6183L14.9998 15.9641L9.34558 21.6183C9.07931 21.8846 8.64761 21.8846 8.38134 21.6183C8.11507 21.352 8.11507 20.9203 8.38134 20.6541L14.0356 14.9998L8.38134 9.34558C8.11507 9.07931 8.11507 8.64761 8.38134 8.38134C8.64761 8.11507 9.07931 8.11507 9.34558 8.38134L14.9998 14.0356Z" fill="white"/>
          </svg>
        </button>
      </div>
      <div class="p-3 bg-white">
        <p></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ServiceTermModal",
  data() {
    return {
      /**
       * 0: close
       * 1: open
       */
      status: 0,

    }
  },
  methods: {
    openModal() {
      const _data = this.$data;

      _data.status = 1;
    },

    closeModal() {
      const _data = this.$data;

      _data.status = 0;
    }
  }
}
</script>

<style scoped>

</style>

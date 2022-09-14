<template>
  <div class="header-box d-flex flex-column px-3 py-4 justify-content-center">
    <div class="d-flex w-100 position-relative">
      <div class="left position-absolute">
        <button class="btn-back d-flex bg-white border-0 p-0 justify-content-center align-items-center">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="24" height="24" fill="white" fill-opacity="0.01"/>
            <path d="M14.7929 4.29289C15.1834 3.90237 15.8166 3.90237 16.2071 4.29289C16.5676 4.65338 16.5953 5.22061 16.2903 5.6129L16.2071 5.70711L9.415 12.5L16.2071 19.2929C16.5676 19.6534 16.5953 20.2206 16.2903 20.6129L16.2071 20.7071C15.8466 21.0676 15.2794 21.0953 14.8871 20.7903L14.7929 20.7071L7.29289 13.2071C6.93241 12.8466 6.90468 12.2794 7.2097 11.8871L7.29289 11.7929L14.7929 4.29289Z" fill="black"/>
          </svg>
        </button>
      </div>
    </div>

    <h5 class="mb-0 text-center">{{ title }}</h5>
  </div>
</template>

<script>
export default {
  name: "HeaderBox",
  props: {
    title: String
  }
}
</script>

<style scoped>
  .left {
    left: 0;
  }
</style>

<template>
  <div class="d-flex flex-column mb-3">
    <div class="input-group flex-column mb-1">
      <div class="mb-2 d-flex">
        <span class="neoguri-font-weight-500 mb-0">
          <slot name="title"></slot>
        </span>
      </div>
      <template v-if="address === ''">
        <input type="text" placeholder="우편번호 찾기" readonly @click="searchAddress" class="py-3 px-4"/>
      </template>

      <template v-if="address !== ''">
        <input type="text" name="address" v-model="address" readonly class="py-3 px-4"/>
        <input type="text" name="address_detail" placeholder="상세주소(50자까지 입력 가능)" v-model="addressDetail" class="py-3 px-4"/>

      </template>

    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend(
  {
    name: 'NeoguriAddressInput',
    props: {
    },
    data() {
      return {
        address: '',
        addressDetail: '',

        isConfirmed: false
      }
    },
    methods: {
      searchAddress() {
        const _data = this.$data;

        new daum.Postcode({
          oncomplete: (data: any) => {
            const addr = data.roadAddress;
            let extraAddr = '';

            if(data.userSelectedType === 'R'){
              if(data.bname !== '' && /[동|로|가]$/g.test(data.bname)){
                extraAddr += data.bname;
              }

              if(data.buildingName !== '' && data.apartment === 'Y'){
                extraAddr += (extraAddr !== '' ? ', ' + data.buildingName : data.buildingName);
              }

              if(extraAddr !== ''){
                extraAddr = ' (' + extraAddr + ')';
              }
            }

            _data.address =  `[${data.zonecode}] ${addr} ${extraAddr}`;
          }
        }).open();
      },
    },
    watch: {
      address() {
        const _data = this.$data;
        const payload = {
          address: _data.address,
          addressDetail: _data.addressDetail
        };

        this.$emit('input', payload);
      },
      addressDetail() {
        const _data = this.$data;
        const payload = {
          address: _data.address,
          addressDetail: _data.addressDetail
        };

        this.$emit('input', payload);
      }
    }

  })
</script>

<style scoped>

  input {
   border: 1px solid #DFDFDF;
  }

  input::placeholder {
    color: #949494;
  }

</style>

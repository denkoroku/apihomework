<template lang="html">
  <div class="row">
    <div class="">
      <label for="currencySelect">currency</label>
      <select
      v-on:change="handleSelectCurrency"
      id="currency"
      class="form-control"
      v-model="selectedCurrencyCode">
      <option v-for="(currency, index) in cryptoData"
      :key="index":value="currency.symbol">{{currency.name}}</option>
    </select>
  </div>
</div>
</template>

<script>
import { eventBus } from '@/main.js';
export default {
  props:['cryptoData'],

  data(){
    return{
      selectedCurrencyCode:this.selectedCurrencyCode,

    }
  },
  methods: {
    handleSelectCurrency() {
        const selectedCurrency = this.cryptoData
        .find(currency => currency.symbol === this.selectedCurrencyCode);
        eventBus.$emit('currency-selected', selectedCurrency);

      },
    }
  }

</script>

<style lang="css" scoped>
</style>

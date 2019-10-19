<template lang="html">
  <div class="row">
      <div class="">
          <label for="currencySelect">currency</label>
          <select
                  id="currency"
                  class="form-control"
                  v-model="selectedCurrency">
              <option v-for="currency in cryptoCurrencies">{{currency}}</option>
          </select>
      </div>
  </div>
</template>

<script>
export default {
  props:['cryptoCurrencies'],
  data(){
    return{
      selectedCurrency:"ethereum"
    }

  }


}
</script>

<style lang="css" scoped>
</style>

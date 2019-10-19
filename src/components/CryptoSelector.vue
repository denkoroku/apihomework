<template lang="html">
  <div class="row">
      <div class="">
          <label for="currencySelect">currency</label>
          <select
                  id="currency"
                  class="form-control"
                  v-model="selectedCurrency">
              <option v-for="currency in cryptoData">{{currency.name}}</option>
          </select>
      </div>
  </div>
</template>

<script>
export default {
  props:['cryptoData'],
  data(){
    return{
      selectedCurrency:""
    }
  },


}
</script>

<style lang="css" scoped>
</style>

<!-- if(this.cryptoData){
  const preparedData = this.cryptoData.slice(0,10);
  const chartData = this.preparedData.map((currencyObject)=>{
    return [currencyObject.name, currencyObject.current_price]
  })
  chartData = this.chartData
}
return null -->

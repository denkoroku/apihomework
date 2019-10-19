<template lang="html">
  <div>
    <GChart
    v-if="testData"
    type="ColumnChart"
    :data="testData"
    :options="chartOptions"
    />
  </div>

</template>

<script>
import { GChart } from 'vue-google-charts'
export default {
  name: 'crypto-chart',
  props:['cryptoData'],

  data(){
    return {
      testData:[['name','current_price'],["bitcoin",500],["ethereum",200],["bananacoin",10]],
      chartData: null,
      chartOptions: {
        width: 800,
        height: 240,
        title: 'Top 10 cryptocurrencies',
      },

      components: {
        GChart
      },
      computed: {
        chartData: function(){
          if(this.cryptoData){
            const preparedData = this.cryptoData.slice(0,10);
            const chartData = this.preparedData.map(data => Object.values(data))
            chartData[0] = Object.keys(this.preparedData[0])
            console.log(chartData);
            return chartData;
            }
          return null
        }
      }
    }
  }
}
</script>

<style lang="css" scoped>
</style>




<!-- old -->
<!-- chartData: function(){
  if(this.cryptoData){
    const preparedData = this.cryptoData.slice(0,10);
    const chartData = this.preparedData.map((currencyObject)=>{
      return [currencyObject.name, currencyObject.current_price]
    })
    chartData = this.chartData
  }
  return null
} -->

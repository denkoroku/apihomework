<template lang="html">
  <GChart
    v-if="chartData"
    type="ColumnChart"
    :data="chartData"
    :options="chartOptions"
  />
</template>

<script>
import { GChart } from 'vue-google-charts'
export default {
  name: 'crypto-chart',
  data(){
    return {
      chartOptions: {
        width: 800,
        height: 240,
        title: 'Top 10 cryptocurrencies',
      }
    }
  },
  props: ['cryptoData'],
  components : {
    GChart
  },
  computed: {
    chartData: function(){
      if(this.chartData){
        const chartData = this.cryptoData.map((currencyObject)=>{
          return [currencyObject.name, currencyObject.current_price]
        }
        return chartData
      }
      return null
    }
  }
}
</script>

<style lang="css" scoped>
</style>

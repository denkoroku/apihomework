<template lang="html">
  <div>

    <GChart
    v-if="chartData"
    type="ColumnChart"
    :data="chartData"
    :options="chartOptions"
    />

    </div>

  </template>

  <script>
  import { GChart } from 'vue-google-charts'
  export default {
    name: 'crypto-chart',
    data(){
      return {
      chartData: null,
        chartOptions: {
          width: 800,
          height: 240,
          title: 'Top 10 cryptocurrencies',
        },

        props:['cryptoData'],
        components: {
          GChart
        },
        computed: {
          chartData: function(){
            if(this.cryptoData){
              const preparedData = this.cryptoData.slice(0,10);
              const chartData = this.preparedData.map((currencyObject)=>{
                return [currencyObject.name, currencyObject.current_price]
              })
               chartData = this.chartData
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

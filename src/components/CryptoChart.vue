<template lang="html">
  <div class="">
    <h3> Percent Change over last 24hrs</h3>
    <GChart
    type="ColumnChart"
    :data='chartData'
    :options='chartOptions'
    class="chart"/>
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'crypto-chart',
  props: ['cryptoData'],
  components: {
    GChart
  },
  data () {
    return {
      chartOptions: {
        width: 1000,
        height: 500,
        legend:'none',
        chart: {
          title: 'Crypto Chart',
        }
      }
    }
  },
  computed: {
    chartData: function() {
      if (!this.cryptoData) return;
      const smallData = this.cryptoData.slice(0,10)
      const chartData = smallData.map((item) => {
        return [item.name, item.price_change_percentage_24h]
      })
      chartData.unshift(['Name', 'Current Price'])
      return chartData
    }
  },
}


</script>

<style lang="css">

body {
  display: flex;
  justify-content: center;
}
</style>

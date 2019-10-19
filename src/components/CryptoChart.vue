<template lang="html">
  <div class="">
    <h2> Chart</h2>
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
        width: 800,
        height: 1040,
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
        return [item.name, item.current_price]
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

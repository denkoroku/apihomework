<template>
  <div id="app">
    <h1>Cryptocurrency Tracker</h1>

    <crypto-chart  :cryptoData="cryptoData"> </crypto-chart>
    <crypto-selector :cryptoData="cryptoData">  {{selectedCurrency}}</crypto-selector>
  </div>
</template>

<script>

import CryptoSelector from './components/CryptoSelector.vue';
import CryptoChart from './components/CryptoChart.vue';

export default {
  name: 'app',
  components: {
    "crypto-selector":CryptoSelector,
    "crypto-chart":CryptoChart
  },
  data(){
    return {
      cryptoData: null,
      cryptoCurrencies:['bitcoin', 'ethereum', 'bananacoin'],
      selectedCurrency:null
    }
  },
  mounted(){
    fetch("https://api.coingecko.com/api/v3/coins/markets?vs_currency=gbp&order=market_cap_desc&per_page=100&page=1&sparkline=false&price_change_percentage=1h%2C24h%2C7d")
    .then(response => response.json())
    .then(json => {
      this.cryptoData = json
    })

  }
}

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>

<!-- old -->
<!-- .then(response => response.json())
.then(json => this.cryptoData = json)
.then (cryptoData => console.log(cryptoData)) -->

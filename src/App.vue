<template>
  <div id="app">
    <h1>Cryptocurrency Tracker</h1>

    <crypto-chart  :cryptoData="cryptoData"> </crypto-chart>
    <crypto-selector :cryptoData="cryptoData">  {{selectedCurrency}}</crypto-selector>
    <crypto-details v-if="selectedCurrency" :cryptoData="cryptoData" :currency="selectedCurrency"></crypto-details>
  </div>
</template>

<script>
import CryptoSelector from './components/CryptoSelector.vue';
import CryptoChart from './components/CryptoChart.vue';
import CryptoDetails from './components/CryptoDetails.vue';
import { eventBus } from '@/main.js';
export default {
  name: 'app',
  components: {
    "crypto-selector":CryptoSelector,
    "crypto-chart":CryptoChart,
    "crypto-details":CryptoDetails,
  },
  data(){
    return {
      cryptoData: null,
      selectedCurrency:null
    }
  },
  mounted(){
    fetch("https://api.coingecko.com/api/v3/coins/markets?vs_currency=gbp&order=market_cap_desc&per_page=100&page=1&sparkline=false&price_change_percentage=1h%2C24h%2C7d")
    .then(response => response.json())
    .then(json => {
      this.cryptoData = json
    });
    eventBus.$on('currency-selected', (currency) => {
      this.selectedCurrency = currency
    });
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

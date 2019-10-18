<template>
  <div id="app">
    <h1>Cryptocurrency Tracker</h1>
    <crypto-selector cryptocurrency="Bitcoin"></crypto-selector>

  </div>
</template>

<script>

import CryptoSelector from './components/CryptoSelector.vue';
export default {
  name: 'app',
  components: {
    "crypto-selector":CryptoSelector
  },
  data(){
    return {

    }
  },

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

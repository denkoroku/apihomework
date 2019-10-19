<template lang="html">
  <div v-if="currency" id="currencyDetail">
    <h2>{{ currency.name }}</h2>
    <img>{{currency.image}}</img>
    <dl>
      <dt>Market Cap:</dt>
      <dd>{{ currency.market_cap }}</dd>
      <dt>Current Price:</dt>
      <dd>{{ currency.current_price }}</dd>
    </dl>
  </div>
</template>

<script>
export default {
  name: 'currency-details',
  props: ['cryptoData', 'currency']
}
</script>

<style lang="css" scoped>
</style>

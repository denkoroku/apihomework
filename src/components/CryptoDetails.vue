<template lang="html">
  <div v-if="currency" id="currencyDetail">
    <h2>{{ currency.name }}</h2>
    <img :src="currency.image" :alt="currency.name">
    <table>
      <tr>
      <th>Market Cap:</th>
      <td>{{ currency.market_cap }}</td></tr>
      <tr>
        <th>Current Price:</th>
      <td>{{ currency.current_price }}</td></tr>
      <tr>
        <th>Highest in this 24hrs:</th>
      <td>{{ currency.high_24h }}</td></tr>
      <tr>
        <th>Lowest in this 24hrs:</th>
      <td>{{ currency.low_24h }}</td></tr>

    </table>
  </div>
</template>

<script>
export default {
  name: 'crypto-details',
  props: ['cryptoData', 'currency'],

}
</script>

<style lang="css" scoped>
img{
  display:inline-flex;
  float:left;
  width:100px;
  margin:130px;
margin-top: -50px;

}
</style>

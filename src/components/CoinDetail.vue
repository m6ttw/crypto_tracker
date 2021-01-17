<template lang="html">
  <div v-if='coin'>
    <h2>Coin Details</h2>
    <h3>({{coin.symbol}}) {{coin.name}}</h3>
    <p>{{coin.rank}}</p>
    <p>Price: ${{coin.price_usd}}</p>
    <p>Change (%):
      <br>1h: {{coin.percent_change_1h}}
      <br>24h: {{coin.percent_change_24h}}
      <br>7 days: {{coin.percent_change_7d}}
    </p>
    <p>Market Cap: ${{coin.market_cap_usd}}</p>
    <button v-on:click="trackCoin">Track</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'coin-detail',
  props: ['coin'],
  methods: {
    trackCoin: function() {
      eventBus.$emit("coin-tracked", this.coin);
    }
  }
}
</script>

<style lang="css" scoped>
</style>

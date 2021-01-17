<template lang="html">
  <div v-if='coin'>
    <h1>({{coin.symbol}}) {{coin.name}}</h1>
    <button id="track" v-on:click="trackCoin">Track</button>
    <h3>Price: ${{coin.price_usd}}</h3>
    <p><b>Change (%):</b>
      <br>1h: {{coin.percent_change_1h}}
      <br>24h: {{coin.percent_change_24h}}
      <br>7 days: {{coin.percent_change_7d}}
    </p>
    <p><b>Market Cap: ${{coin.market_cap_usd}}</b>
      <br>(Rank: {{coin.rank}})
    </p>
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
div {
  height: 340px;
  width: 500px;
  padding:30px;
  border: 2px solid rgb(0, 0, 0);
  margin-left: 20px;
  text-align: center;
}
#track {
  cursor: pointer;
  border: 2px solid rgb(42, 235, 51);
  background-color: rgb(42, 235, 51);
}
#track:active {
  background-color: rgb(0, 0, 0);
  color: rgb(42, 235, 51);
}
</style>

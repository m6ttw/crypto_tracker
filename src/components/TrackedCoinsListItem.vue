<template>
  <li id="tracked"><h3>({{coin.symbol}}) {{ coin.name }}<br></h3>
    <p id="price"><b>Price: ${{coin.price_usd}}</b></p>
    <p><b>Change (%):</b>
      <br>1h: {{coin.percent_change_1h}}
      <br>24h: {{coin.percent_change_24h}}
      <br>7 days: {{coin.percent_change_7d}}
    </p>
    <p>Market Cap: ${{coin.market_cap_usd}}</p>
    <button id="stop" v-on:click="stopTracking">Stop Tracking</button></li>
</template>

<script>
import { eventBus } from "../main.js";

export default {
  props: ["coin"],
  methods: {
    stopTracking: function() {
      eventBus.$emit("tracking-stopped", this.coin);
    }
  }
};
</script>

<style>
#tracked {
  border: 2px solid rgb(0, 0, 0);
  padding-left: 20px;
  padding-right: 20px;
  padding-bottom: 20px;
}
  /* h3 {
    text-align: center;
  }; */
  #stop {
    cursor: pointer;
  }
  /* #price {
    text-align: center;
  } */
</style>
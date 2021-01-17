<template>
  <li><h4>({{coin.symbol}}) {{ coin.name }}<br></h4>
    <p>Price: ${{coin.price_usd}}</p>
    <p>Change (%):
      <br>1h: {{coin.percent_change_1h}}
      <br>24h: {{coin.percent_change_24h}}
      <br>7 days: {{coin.percent_change_7d}}
    </p>
    <p>Market Cap: ${{coin.market_cap_usd}}</p></li>
</template>

<script>
export default {
  props: ["coin"]
};
</script>

<style>

</style>
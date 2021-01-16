<template>
  <div>
    <h1>Crypto Top 50</h1>
    <div class="main-container">
      <coins-list :coins='coins'></coins-list>
      <coin-detail :coin='selectedCoin'></coin-detail>
    </div>
  </div>
</template>

<script>
import CoinsList from './components/CoinsList';
import CoinDetail from './components/CoinDetail';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return {
      coins: [],
      selectedCoin: null
    };
  },
  mounted(){
    fetch('https://api.coinpaprika.com/v1/ticker')
    .then(res => res.json())
    .then(coins => this.coins = coins)

    eventBus.$on('coin-selected', (coin) => {
      this.selectedCoin = coin
    })
  },
  components: {
    "coins-list": CoinsList,
    "coin-detail": CoinDetail
  }
}
</script>

<style lang="css" scoped>
  h1 {
    text-align: center;
  }
  .main-container {
    display: flex;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;
  }
</style>

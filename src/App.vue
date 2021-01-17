<template>
  <div>
    <h1>CRYPTO TRACKER</h1>
    <tracked-coins-list :trackedCoins="tracked"></tracked-coins-list>
    <div class="main-container">
      <coins-list :coins='coins'></coins-list>
      <coin-detail :coin= "selectedCoin"></coin-detail>
    </div>
    <p>Data from Coinpaprika</p>
  </div>
</template>

<script>
import CoinsList from './components/CoinsList';
import CoinDetail from './components/CoinDetail';
import TrackedCoinsList from "./components/TrackedCoinsList";
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return {
      coins: [],
      selectedCoin: null,
    };
  },
  computed: {
    tracked: function() {
      return this.coins.filter(coin => coin.isTracked);
    }
  },
  methods: { 
    getCoins: function(){
      fetch('https://api.coinpaprika.com/v1/ticker')
        .then(res => res.json())
        .then(coinData => {
          coinData.forEach(coin => (coin.isTracked = false));
          coinData.forEach(coin => (coin.rank = parseInt(coin.rank)))
          this.coins = coinData;
        })
        .then(() => this.sortCoins("rank"));
    },
    sortCoins: function(property) {
      this.coins.sort((a, b) => {
        return a[property] < b[property] ? -1 : 1;
      });
    },
    markTracked: function(coin) {
      const index = this.coins.indexOf(coin);
      this.coins[index].isTracked = true;
    },
    unmarkTracked: function(coin) {
      const index = this.coins.indexOf(coin);
      this.coins[index].isTracked = false;
    }
  },
  mounted(){
    this.getCoins();

    eventBus.$on('coin-selected', (coin) => {
      this.selectedCoin = coin
    });

    eventBus.$on("coin-tracked", coin => this.markTracked(coin));

    eventBus.$on("tracking-stopped", coin => this.unmarkTracked(coin));
  },
  components: {
    "coins-list": CoinsList,
    "coin-detail": CoinDetail,
    "tracked-coins-list": TrackedCoinsList
  }
}
</script>

<style lang="css" scoped>
  h1 {
    text-align: center;
    padding-top: 10px;
    padding-bottom: 20px;
  }
  p {
    padding-top: 10px;
    padding-bottom: 10px;
    padding-left: 10px;
  }
  .main-container {
    display: flex;
    justify-content: space-between;
    width: 80%;
    margin: 0 auto;
  }
</style>

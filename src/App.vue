<template>
	<div id="app">
		<h1>Crypto Tracker</h1>
		<h4>Data provided by Coinranking</h4>
		<coins-list :coins="coins"></coins-list>
	</div>
</template>

<script>
import CoinsList from "./components/CoinsList.vue";
import { eventBus } from "./main.js";

export default {
	name: 'app',
	data() {
		return {
		coins: [],
		selectedCoin: null
		};
	},
	mounted() {
		fetch ("https://api.coinranking.com/v2/coins")
		.then(res => res.json())
		.then(coins => this.coins = coins)

		eventBus.$on("coin-selected", (coin) => {
			this.selectedCoin = coin
		})
  	},
  	components: {
	  	"coins-list": CoinsList
	},
}
</script>

<style></style>
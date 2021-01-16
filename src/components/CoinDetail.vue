
<template lang="html">
  <div v-if='coin'>
    <h3>({{coin.symbol}}) {{coin.name}}</h3>
    <p>Price: ${{coin.price_usd}}</p>
    <p>Change (%):
      <br>1h: {{coin.percent_change_1h}}
      <br>24h: {{coin.percent_change_24h}}
      <br>7 days: {{coin.percent_change_7d}}
    </p>
    <p>Market Cap: ${{coin.market_cap_usd}}</p>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'coin-detail',
  props: ['coin']
}
</script>

<style lang="css" scoped>
</style>


data () {
        return {
            list: [],
            timer: ''
        }
    },
    created () {
        this.fetchEventsList();
        this.timer = setInterval(this.fetchEventsList, 300000)
    },
    methods: {
        fetchEventsList () {
            this.$http.get('events', (events) => {
                this.list = events;
            }).bind(this);
        },
        cancelAutoUpdate () { clearInterval(this.timer) }

    },
    beforeDestroy () {
      clearInterval(this.timer)
    }
});
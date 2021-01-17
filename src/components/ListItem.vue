<template lang="html">
  <div>
    <li v-on:click="handleClick">{{coin.rank}}. {{coin.name}} ({{coin.symbol}})</li>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'list-item',
  props: ['coin'],
  methods: {
    handleClick(){
      eventBus.$emit('coin-selected', this.coin)
    }
  }
}
</script>

<style lang="css" scoped>
  li {
    padding-top: 5px;
    padding-bottom: 5px;
    padding-right: 10px;
    padding-left: 10px;
  }
  li:hover {
    background-color: black;
    color: white;
    cursor: pointer;
  }
</style>

<template lang="html">
  <div>
    <li v-on:click="handleClick">{{coin.name}}</li>
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
</style>

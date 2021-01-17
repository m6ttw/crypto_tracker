<template lang="html">
  <div>
    <h2>Crypto Top 50</h2>
    <ol>
      <list-item v-for="(coin, index) in coins" :coin="coin" :key="index" v-if="index < 50"></list-item>
    </ol>
  </div>

</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'coins-list',
  props: ['coins'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>

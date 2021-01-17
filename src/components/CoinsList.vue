<template lang="html">
  <div id="coinsList">
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
  #coinsList {
    /* background: #eee; */
    height: 400px;
    overflow-y: scroll;
    border: 2px solid rgb(0, 0, 0);
  }
  #coinsList ul {
    margin: 10px;
    padding: 0;
  }
  ol {
    padding-left: 15px;
    padding-right: 15px;
    list-style-type: none;
  }
  ::-webkit-scrollbar {
    /* -webkit-appearance: none; */
    width: 7px;
  }
  ::-webkit-scrollbar-thumb {
    /* border-radius: 4px; */
    background-color: black;
    -webkit-box-shadow: 0 0 1px rgba(255,255,255,.5);
  }
</style>

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
    margin-right: 20px;
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
    width: 7px;
    background-color: rgb(200, 200, 200);
  }
  ::-webkit-scrollbar-thumb {
    background-color:grey;
    box-shadow: white;
    -webkit-box-shadow: 0 0 1px rgba(255,255,255,.5);
  }
</style>

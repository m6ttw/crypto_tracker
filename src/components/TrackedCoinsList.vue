<template>
  <div id="tracked-coins-list">
    <ul>
      <tracked-coins-list-item v-for="(coin, index) in trackedCoins" :coin="coin" :key="index"></tracked-coins-list-item>
    </ul>
  </div>
</template>

<script>
import TrackedCoinsListItem from './TrackedCoinsListItem.vue'
export default {
  props: ["trackedCoins"],
  components: {
    "tracked-coins-list-item": TrackedCoinsListItem
  }
}
</script>

<style>
  ul {
    display: flex;
    justify-content: space-around;
  }
</style>
TrackedCoinsListItem
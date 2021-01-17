<template>
  <div class="tracked-coins-list">
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
  .tracked-coins-list {
    margin-left: 65px;
    margin-right: 105px;
  }
  ul {
    display: flex;
    justify-content: center;
    list-style-type: none;
  }
</style>
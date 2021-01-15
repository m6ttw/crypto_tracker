<template>
	<div>
		<ul>
			<list-item v-for="(coin, index) in coins" :coin="coin" :key="index"></list-item>
		</ul>
  	</div>
</template>

<script>
import ListItem from "./ListItem.vue";

export default {
	name: "coins-list",
  	props: ["coins"],
  	components: {
    "list-item": ListItem
  }
}
</script>

<style></style>
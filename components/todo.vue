<template>
	<ul>
		<li v-for="(list, i) in lists" :key="i">「{{list.title}}」 {{list.body}}<button @click="clear(i)">削除</button></li>
	</ul>
</template>

<script>
import Vue from "../pages/index.vue"

export default {
	props: ['lists'],
	methods: {
		clear: function (i) {
			this.lists.splice(i,1)
			this.$emit('save')
		}
	}
}
</script>

<style>

</style>
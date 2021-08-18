<template>
	<ul>
		<li v-for="(list, i) in lists" :key="i">「{{list.title}}」 {{list.body}}</li>
	</ul>
</template>

<script>
export default {
	props: ['lists']
}
</script>

<style>

</style>
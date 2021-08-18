<template>
 <div>
   <ul>
		<li v-for="(list, i) in lists" :key="i">「{{list.title}}」 {{list.body}}<button @click="clear(i)">削除</button></li>
	</ul>
  <p>{{ lists }}</p>
 </div>
	
</template>

<script>

export default {
	props: ['lists'],
	methods: {
		clear: function (i) {
			this.lists.splice(i,1)
			localStorage.setItem('lists', JSON.stringify(this.lists));
		},
	}
}
</script>

<style>

</style>
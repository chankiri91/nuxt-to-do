<template>
	<button @click="clear(i)">削除</button>
</template>

<script>
export default {
	 clear: function(i) {
      this.lists.splice(i,1)
      this.save()
    }
}
</script>

<style>

</style>
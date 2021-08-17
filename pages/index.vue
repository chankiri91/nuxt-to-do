<template>
  <div id="app">
    <h1>Nuxt To Do App</h1>
    <div>
      <label for="title">タイトル：</label>
      <input type="text" v-model="title" placeholder="タイトル">
    </div>
    <div>
      <label for="body">内容：</label>
      <input type="text" v-model="body" placeholder="内容">
    </div>
    <div>
      <input type="submit" value="追加" @click="add">
    </div>
    <div>
      <ul v-for="(list, i) in lists" v-bind:key="i">
        <li>「{{list.title}}」, 詳細:{{list.body}}<button @click="clear(i)">削除</button></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    lists: [
      {title: '買い物', body: '牛乳を買う'},
      {title: '宿題', body: '数学12~24ページ'}
    ]
  }),
  methods: {
    clear: function(i) {
      this.lists.splice(i,1)
    },
    add: function() {
      if(this.title === '' || this.body === '')return

      this.lists.push({title: this.title, body: this.body})
      this.title = ''
      this.body = ''
    }
  }
}
</script>

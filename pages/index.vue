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
      <!-- <todo v-for="(list, i) in lists" v-bind="lists" v-bind:key="i"></todo> -->
      <Todo :lists="lists"/>
    </div>
  </div>
</template>

<script>
import Todo from '../components/todo.vue'


export default {
  data: () => ({
    lists: [
      {title: '買い物', body: '牛乳を買う'},
      {title: '宿題', body: '数学12~24ページ'}
    ],
  }),
  components: {
    Todo
  },
  methods: {
    clear: function(i) {
      this.lists.splice(i,1)
      this.save()
    },
    add: function() {
      if(this.title === '' || this.body === '')return

      this.lists.push({title: this.title, body: this.body})
      this.title = ''
      this.body = ''
      this.save()
    },
    save: function() {
      localStorage.setItem('lists', JSON.stringify(this.lists));
    },
    load: function() {
      this.lists = JSON.parse( localStorage.getItem('lists') )
      if( !this.lists ){
        this.items = []
      }
    }
  },
  mounted: function() {
    this.load()
  }
}
</script>

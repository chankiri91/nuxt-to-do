<template>
  <div id="app">
    <h1>Nuxt To Do App</h1>
    <div class="title-and-body">
      <div>
        <label for="title" >タイトル：</label>
        <input type="text" v-model="title" placeholder="タイトル">
      </div>
      <div>
        <label for="body">内容：</label>
        <input type="text" v-model="body" placeholder="内容">
        <input type="submit" value="追加" @click="add">
        <input type="submit" value="編集" @click="edit(index)">
      </div>
    </div>
    <div class="hensyu">
      <label for="hensyu">編集したいもの：</label>
      <input type="number" v-model="index" :disabled="banme">
      <button @click="hensyu(index)" v-model="index">番目</button>
    </div>
    <div>
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
    title: '',
    body: '',
    index: 1,
    banme: false
  }),
  components: {
    Todo,
  },
  methods: {
    add() {
      if(this.title === '' || this.body === '')return

      this.lists.push({title: this.title, body: this.body})
      this.title = ''
      this.body = ''
    },
    hensyu(index) {
      if(index > this.lists.length || index <= 0) {
        alert('存在しません')
        return
      }
      this.title = this.lists[index-1].title
      this.body = this.lists[index-1].body
      this.banme = true
    },
    edit(index) {
      if(this.title === '' || this.body === '')return

      this.lists.splice(index-1, 1, {title: this.title, body: this.body})
      this.title = ''
      this.body = ''
      this.banme = false
    },
  },
}
</script>

<style lang="scss">
  #app {
    font-size: 30px;
    text-align: center;
    line-height: 2;
    h1 {
      color: red;
      font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
      border-bottom: 1px solid black;
    }
    .title-and-body{
      border: 1px solid black;
    }
  }
</style>>

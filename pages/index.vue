<template>
  <div id="app">
    <h1>Nuxt To Do App</h1>
    <div>
      <ul v-for="(list, i) in lists" v-bind:key="i">
        <li>「{{list.title}}」, 詳細:{{list.body}}</li>
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
  })
}
</script>

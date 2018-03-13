<template>
  <div id="app">
    <EditorView @add="add" />
    <ListItem :memo="memo" />
  </div>
</template>

<script>
import ListItem from './components/ListItem'
import EditorView from './components/EditorView'

export default {
  name: 'App',
  components: {
    ListItem,
    EditorView
  },
  data () {
    return {
      memo: {
        id: 1,
        text: '',
        date: '',
        tags: ''
      }
    }
  },
  methods: {
    add (newMemo) {
      console.log(newMemo)
      Object.assign(this.memo, newMemo)
    }
  }
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
</style>

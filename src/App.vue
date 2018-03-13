<template>
  <div id="app">
    <EditorView @add="add" />
    <ListView :memos="memos" />
  </div>
</template>

<script>
import EditorView from './components/EditorView'
import ListView from './components/ListView'

export default {
  name: 'App',
  components: {
    EditorView,
    ListView
  },
  data () {
    return {
      memos: []
    }
  },
  methods: {
    add (newMemo) {
      newMemo.id = this.nextId
      this.memos.push(newMemo)
    }
  },
  computed: {
    nextId () {
      // this.memos の中で一番大きい id + 1 を返す
      return this.memos.reduce((id, memo) => {
        return id < memo.id ? memo.id : id
      }, 0) + 1
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

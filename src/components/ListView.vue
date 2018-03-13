<template lang=pug>
  .list-view
    div(v-if="memos && memos.length !== 0")
      list-item(
        v-for="memo in memos"
        :key="memo.id"
        :memo="memo"
      )
    div(v-else) 表示できるメモがありません。
</template>

<script>
import ListItem from './ListItem'

export default {
  name: 'ListView',
  components: {
    ListItem
  },
  props: {
    memos: Array
  }
}
</script>

<style lang="scss">
.list-view {
  border-top: 1px solid #ddd;
}
</style>

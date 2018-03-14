<template lang=pug>
  .list-item
    div
      span id
      span {{memo.id}}
    div
      span text:
      span {{memo.text}}
    div
      span date:
      span {{memo.date}}
    div
      span tag:
      span
        span(v-for="tag in memo.tags" :key="tag.id") {{tag}}
    div
      button(@click="remove(memo.id)") 削除
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    memo: Object
  },
  methods: {
    remove (id) {
      this.$parent.$emit('remove', id)
    }
  }
}
</script>

<style lang=scss scoped>
.list-item {
  position: relative;
  padding: 5px;
  border-bottom: 1px solid #ddd;
  font-size: 12px;

  &:nth-of-type(2n + 1) {
    background-color: #f6f6f6;
  }

  & > div > span:nth-of-type(1) {
    display: inline-block;
    min-width: 26px;
  }

  & > div span:nth-of-type(2) span {
    font-size: 10px;
    background-color: #555;
    color: #fff;
    padding: 3px 5px;
    position: relative;
    margin-right: 5px;
  }

  & > div:nth-of-type(5) button {
    cursor: pointer;
    border: none;
    color: #fff;
    background-color: tomato;
    position: absolute;
    top: 5px;
    right: 5px;
    display: none;
  }

  &:hover > div:nth-of-type(5) button {
    display: block;
  }
}
</style>

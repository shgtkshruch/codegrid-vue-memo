<template lang=pug>
  .editor-view
    div
      label 内容：
      input(v-model="input.text" placeholder="メモのタイトル")
    div
      label 日付：
      input(type="date" v-model="input.date")
    div
      label タグ：
      input(v-model="input.tags" placeholder="空白区切りで指定")
    div
      button(@click="save") 保存
</template>

<script>
export default {
  name: 'EditorView',
  data () {
    return {
      input: {
        text: '',
        date: '',
        tags: ''
      }
    }
  },
  computed: {
    tagsArr () {
      // input.tags の文字列を空白で区切って配列に変換する
      return this.input.tags.trim() !== '' ? this.input.tags.trim().split(/\s+/) : []
    }
  },
  methods: {
    save () {
      // this.input のクローンを生成する
      const data = Object.assign({}, this.input, {tags: this.tagsArr})
      // 'add'イベントを自身にトリガーする
      this.$emit('add', data)
    }
  }
}
</script>

<style lang=scss>

.editor-view {
  flex-grow: 1;
  border-radius: 2px;
  height: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  max-width: 400px;
  padding: 10px;

  & > div {
    box-shadow: 0 1px 0 rgba(255,255,255, 1);
    background-color: #fff;
    font-size: 14px;
    display: flex;
    align-items: center;
    margin-bottom: 5px;
  }

  & > div label {
    color: #555;
    font-size: 11px;
    min-width: 35px;
    text-align: right;
  }

  & > div input {
    flex-grow: 1;
    box-sizing: border-box;
    padding: 10px 5px;
    outline-offset: -4px;
    outline-width: 1px;
    border: 1px solid #b3b3b3;
  }

  & > div:last-of-type {
    justify-content: flex-end;
    padding: 5px 0 0;
  }

  & button {
    margin-left: 10px;
    background-color: #555;
    color: #fff;
    cursor: pointer;
    border: none;
    width: 100px;
    line-height: 30px;
  }
}

</style>

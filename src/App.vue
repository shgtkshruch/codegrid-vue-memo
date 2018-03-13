<template>
  <div id="app">
    <ListItem />
  </div>
</template>

<script>
import ListItem from './components/ListItem'

export default {
  name: 'App',
  components: {
    ListItem
  }
}
</script>

<style>
body {
  padding: 0;  margin: 0;
}
</style>

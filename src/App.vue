<template>
  <div id="app">
    <NewList/>
  </div>
</template>

<script>
import NewList from './components/NewList'

export default {
  name: 'App',
  components: {
    NewList
  }
}
</script>

<style>
@import './common/css/newList.css';
</style>

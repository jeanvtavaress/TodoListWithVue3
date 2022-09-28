<template>
  <div id="app">
     <TheTodoList />
  </div>
</template>

<script>
import TheTodoList from './components/TheTodoList.vue'
export default {
  name: 'App',
  components: {
    TheTodoList
  }
}
</script>

<style>

body {
    background-color: rgb(101, 145, 212);
  }

#app {
  padding: 2rem;
  font-weight: normal;
}
</style>

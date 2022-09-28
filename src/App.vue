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
  color: #fff;
  background: rgb(95, 30, 43);
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  }

#app {
  padding: 2rem;
  font-weight: normal;
}
</style>

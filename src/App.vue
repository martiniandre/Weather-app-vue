<template>
  <div id="app">
    <Home v-bind:temperature="temperature"/>
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  },
  data: () => {
    return{
      temperature: {
        name:"London",
        temp:"26°",
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
}
html,body{
  min-height: 100vh;
}
*{
  padding:0;
  margin:0;
  box-sizing: border-box;
}
</style>

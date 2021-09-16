<template>
  <div id="app">
    <Home 
    v-bind:temperature="temperature" 
    v-bind:historic="historic"
    v-bind:searchLocation="searchLocation"
    v-bind:updateSearch="updateSearch"
    />
  </div>
</template>

<script>
import Home from './components/Home.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Home
  },
  data: () => {
    return{
      search: 'Jundiai',
      temperature: {},
      historic: [],
    }
  },
  created() {
    this.fetchData()
  },
  
  methods: {
    async fetchData(){
      const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.search}&appid=666b26dc14e7c7a589df1cfe9ad24fbb&units=metric`)
      this.temperature = await response.data
    }, 
    updateSearch($event){
      this.search = $event.target.value
    },
    searchLocation() {
      this.historic.push(this.search)
      this.fetchData()
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

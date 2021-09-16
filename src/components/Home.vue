<template>
  <main class="container">
    <div class="temperature">
      <section>
        <h1>{{temperature.main.temp.toFixed(0)}}º</h1>
        <div class="temp_name">
          <h2>{{temperature.name}}</h2>
          <span>{{temperature.weather[0].main}}</span>
        </div>
      </section>
      </div>
      <div class="temp_details">
          <div class="search">
            <input type="text" placeholder="Next Location" v-on:input="updateSearch($event)">
            <button @click="searchLocation">Search</button>
          </div>
          <div class="history">
            <span v-for="(hist,index) in historic" :key="index">{{hist}}</span>
          </div>
          <div class="details">
           <h3>Weather Details</h3>
           <div>
             <span>Temperature</span>
             <strong>{{temperature.main.temp}}°</strong>
           </div>
             <div>
             <span>Feels Like</span>
             <strong>{{temperature.main.feels_like}}°</strong>
           </div>
           <div>
             <span>Min</span>
             <strong>{{temperature.main.temp_min}}°</strong>
           </div>
           <div>
             <span>Max</span>
             <strong>{{temperature.main.temp_max}}°</strong>
           </div>
           <div>
             <span>Humidity</span>
             <strong>{{temperature.main.humidity}}%</strong>
           </div>
          </div>
      </div>
      <div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'Home',
  props:  {
    temperature: Object,
    search:String,
    historic:Array,
    searchLocation: Function,
    updateSearch: Function,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container{
    min-height: 100vh;
    display: flex;
  }
  .temperature{
    width:60%;
    background: #5AA2D6;
    display: flex;
    align-items: flex-end;
    padding-bottom: 6rem;
    color: #E5EBEF;
  }
  .temperature section{
    width: 80%;
    margin: 0 auto;
    display: flex;
    align-items: center;
    gap: 30px;
  }
  .temperature section h1{
    font-size: 7em;
  }
  .temperature .temp_name h2{
    font-size: 4rem;
  }
  .temperature .temp_name span{
    font-size: 1.3rem;
  }
  .temp_details{
    width:40%;
    background: #436B8A;
    color:#AABCCA;
    padding: 4rem;
  }
   .temp_details .search{
    height: 60px;
    display: flex;
    justify-content: flex-start;
    margin-bottom: 30px;
  }
  .temp_details input{
    width: 80%;
    background: transparent;
    border: 0;
    border-bottom: 1px solid #829FB2;
    margin-right: 10px;
    outline: none;
    font-size: 1rem;
    color:white;
  }
  .temp_details input::placeholder{
    color:#829FB2
  }
  .temp_details button{
    width: 20%;
    border: 0;
    background: #8DAABA;
  }
  .temp_details .history{
    padding-bottom: 30px;
    margin-bottom: 30px;
    border-bottom: 1px solid #829FB2;
    max-height: 30vh;
    overflow-y: auto;
  }
  .temp_details .history span{
    display: block;
    font-size: 1.2rem;
    margin-bottom: 10px;
  }
 .temp_details .details h3,strong{
   color:whitesmoke;
 }
 .temp_details .details h3{
   margin-bottom: 30px;
 }
 .temp_details .details div{
   display: flex;
   justify-content: space-between;
   margin-bottom: 40px;
   font-size: 1.1rem;
 }
</style>

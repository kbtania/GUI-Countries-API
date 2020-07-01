<template>
  <div id="app">
    <h1>Explore The World</h1>
    <AllCountries/>
  </div>
</template>

<script>
import AllCountries from './components/AllCountries.vue';

export default {
  name: 'App',
  components: {
    AllCountries
  },
  data: function(){
    return{
      counter: AllCountries.counter = 0,
    }  
  }
}
</script>

<style>
*{
  background: rgb(231, 248, 155);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
  }
  
  h1{
    font-family: 'Pangolin', cursive;
  }
</style>

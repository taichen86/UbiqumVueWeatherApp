<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <WeatherReport  />
    <HelloWorld msg="Welcome to Your Vue.js App"/>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import WeatherReport from './components/WeatherReport.vue'

export default {
  name: 'app',

  components: {
    HelloWorld,
    WeatherReport
  },

  data(){
    return{
    reports: []
    }
  },

  created(){
    this.getTestData();
  },

  methods: {
    fetchJSON( url, init ) {
        return fetch( url, init ).then( response => {
            console.log( 'response ' + response );
            if( response.ok ){ return response.json(); }
            throw new Error( response.statusText );
        });
      },

    getTestData(){
      console.log( 'get test data' );
      const url = 'city.list.json'
      this.fetchJSON( url , { method: 'GET' }).then( result => {
            console.log( 'result ' + JSON.stringify( result ) );
             

      });
    }


  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

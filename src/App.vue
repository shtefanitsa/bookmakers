<template>
  <div id="app">
    <Bookmakers v-on:BankA="doSomething" msg="Kupuon text " TeamA="Scotland"  TeamB="Wales"/>
    <Bookmakers msg="Kupuon text " TeamA="Ireland"   TeamB="France"/>
    <Bookmakers msg="Kupuon text " TeamA="England"   TeamB="Italy"/>
    {{BankA}}
  </div>
</template>

<script>

import Bookmakers from './components/Bookmakers.vue'

export default {
  name: 'app',
  components: {
    Bookmakers,
    Bookmakers,
    Bookmakers,

  },
  data: function(){
    return {
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #899bad;
  margin-top: 60px;
}
</style>

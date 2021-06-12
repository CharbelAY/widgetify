<template>
  <div id="app">
    <w-navigation :wnavigationconf="nav_conf">
      <template>Hello</template>
    </w-navigation>
  </div>
</template>

<script>
import WNavigation from './components/WNavigation.vue'
const nav_conf = require('./configurations/wnavigation.json');
export default {
  name: 'App',
  data(){
    return{
      nav_conf
    }
  },
  components: {
    WNavigation
  }
}
</script>

<style>

</style>

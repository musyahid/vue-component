<template>
  <div id="app">
    <HelloWorld msg="ALBUMS APPS"/>
    <SearchBox/>
    <!-- <example/> -->
  </div>
</template>

<script>
import './assets/dist/style.css'
import HelloWorld from './components/HelloWorld.vue'
import SearchBox from './components/SearchBox.vue'
// import example from './components/example.vue'


export default {
  name: 'App',
  components: {
    // example
    HelloWorld,
    SearchBox
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

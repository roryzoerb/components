<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <hello></hello> -->
    <headlinenews></headlinenews>
  </div>
</template>

<script>
// import Hello from './components/Hello'
import HeadlineNews from './components/HeadlineNews'

export default {
  name: 'app',
  components: {
    // Hello,
    'headlinenews': HeadlineNews
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

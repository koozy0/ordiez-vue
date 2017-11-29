<template>
  <div id="app">
    <orders></orders>
  </div>
</template>

<script>
  import Orders from './components/Orders'

  export default {
    name: 'app',
    components: {
      Orders
    }
  }
</script>

<style>
html{
    min-height: 100%;/* make sure it is at least as tall as the viewport */
    position: relative;
}

body{
    height: 100%; /* force the BODY element to match the height of the HTML element */
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

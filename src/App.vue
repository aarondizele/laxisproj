<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* color: #2c3e50; */
  color: #444;
}
input, button{
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
}
img{
  width: 100%;
  padding: 0;
  margin: 0;
}
</style>

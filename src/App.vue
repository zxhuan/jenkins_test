<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h2>你好陌生人，会不会奇怪。</h2>
    <h2>你好陌生人，会不会奇怪。</h2>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
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

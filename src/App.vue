<template>
  <div id="app">
    <House/>
  </div>
</template>

<script>
import House from './components/House.vue'

export default {
  name: 'App',
  components: {
    House
  }
}
</script>

<style>
@font-face {
  font-family: "BebasNeue";
  src: url("assets/BebasNeueRegular.ttf");
  src: url("assets/BebasNeueRegular.otf");
}
#app {
  font-family: BebasNeue, monospase, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html,body, #app{
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  background-color: black;
}
</style>

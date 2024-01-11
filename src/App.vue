<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <PrimerasPruebas mensaje="Primeras Pruebas"/>
  <ListaTareas/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import PrimerasPruebas from './components/PrimerasPruebas.vue'
import ListaTareas from './components/ListaTareas.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    PrimerasPruebas,
    ListaTareas
  }
}
</script>

<style>
body {
  background-color: black;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}
</style>

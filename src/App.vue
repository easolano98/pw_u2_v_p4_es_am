<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Contador titulo="Estudiante" valor2="2"></Contador>
  <Contador titulo="Profesor"></Contador>
  <Contador titulo="testTitulo"></Contador>
</template>

<script>

import Contador from './components/Contador.vue'

export default {
  name: 'App',
  components: {
    Contador
  }
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
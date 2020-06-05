<template>
  <div id="app">
    <Calculadora/>
  </div>
</template>

<script>
import Calculadora from './components/Calculadora';

export default {
  name: 'App',
  components: {
    Calculadora,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Baloo+Paaji+2&display=swap');

#app {
  font-family: 'Baloo Paaji 2', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

<template>
  <div id="app">
    <img src="./assets/logo.png">
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator'
import 'simple-css-reset/reset.css';



export default {
  name: 'App',
  components: {
    Calculator,
  }
}
</script>

<style>

</style>

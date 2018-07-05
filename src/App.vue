<template>
  <div id="app">
    <Calculator/>
  </div>
</template>

<script>
import Calculator from './components/Calculator'
import 'simple-css-reset/reset.css'




export default {
  name: 'App',
  components: {
    Calculator,
  }
}
</script>

<style>

@import "https://fonts.googleapis.com/css?family=Roboto";

html {
  font-family: 'Roboto', sans-serif;
}

</style>

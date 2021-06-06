<template>
  <Header />
  <h1>Sample text</h1>
  <Button text="Home" />
  <p>add some space here between the buttons</p>
  <Button text="Start" button_color="green"></Button>
</template>

<script>
import Header from './components/Header.vue'
import Button from './components/Button.vue'

export default {
  name: 'App',
  components: {
    Header,
    Button,
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

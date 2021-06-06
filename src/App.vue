<template>
  <Header />
  <h1>Sample text</h1>
  <Button text="Home" />
  <p>add some space here between the buttons</p>
  <Button text="Start" button_color="green"></Button>
  <audio-recorder 
    upload-url = "./data"
    :attempts="1"
    :time="1"
    :headers="headers"
    :before-recording="callback"
    :pause-recording="callback"
    :after-recording="callback"
    :select-record="callback"
    :before-upload="callback"
    :successful-upload="callback"
    :failed-upload="callback"/>
</template>

<script>
import Header from './components/Header.vue'
import Button from './components/Button.vue'
import AudioRecorder from 'vue-audio-recorder'

export default {
  name: 'App',
  components: {
    Header,
    Button,
    AudioRecorder,
  },
  methods: {
    callback(data) {
      console.debug(data)
    }
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

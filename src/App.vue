<template>
  <Header />
  <h1>Sample text</h1>
  <Button text="Home" />
  <br>
  <Button text="Start recording" button_color="green" action="record"></Button>
  <div>
    <audio-recorder 
    upload-url = "./data/"
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
    <audio-player src="./data/0003.wav" />
  </div>
  
</template>

<script>
import Header from './components/Header.vue'
import Button from './components/Button.vue'
import AudioRecorder from 'vue-audio-recorder' //https://openbase.com/js/vue-audio-recorder/documentation

export default {
  name: 'App',
  components: {
    Header,
    Button,
    AudioRecorder,
  },
  methods: {
    callback(data) { //used for audio-recording thing
      console.log("event" , data)
    },
  },
  data() {
    return {
      headers: {
        'Author': 'SR',
      },
    }
  },
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

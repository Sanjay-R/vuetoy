<template>
  <Header />
  <h1>Sample text</h1>
  <section class="sound-clips"></section>
  <Button text="Home" />
  <br />
  <Button text="Start recording" button_color="green" @click="audioloop()" v-show="showButton.start"></Button>
  <div>
    <!-- <button :action="audioloop()"> lkanijcnsikdc </button> -->
    <Button text="Retry" button_color="red" v-show="showButton.retry" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Button from "./components/Button.vue";
// import AudioRecorder from 'vue-audio-recorder' //https://openbase.com/js/vue-audio-recorder/documentation
//https://github.com/grishkovelli/vue-audio-recorder

export default {
  name: "App",
  components: {
    Header,
    Button,
  },
  methods: {
    callback(data) {
      console.log("event \n", data);
    },
    startButton() {
      //toggle buttons here
      
      //start audio recording
    },
    audioloop() {
      if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
        console.log("getUserMedia supported.");
        navigator.mediaDevices
          .getUserMedia(
            // constraints - only audio needed for this app
            {
              audio: true,
            }
          )

          // Success callback
          .then(function (stream) {
            console.log("Great success!!", stream.log)
          })

          // Error callback
          .catch(function (err) {
            console.log("The following getUserMedia error occurred: " + err);
          });
      } else {
        console.log("getUserMedia not supported on your browser!");
      }
    },
  },
  data() {
    return {
      headers: {
        Author: "SR",
      },
      showButton: {
        start: true,
        retry: false,
        confirm: false,
      },
    };
  },
};
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

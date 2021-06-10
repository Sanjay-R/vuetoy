<template>
  <Header />
  <h1>Sample text</h1>
  <Button text="Home" />
  <br />
  <Button text="Start recording" button_color="green" @click="startButton()" v-show="showButton.start"></Button>
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
    async startButton() {
      //toggle buttons here
      //indicate that a recording has started to the user
      //start audio recording
      const aud = await this.recordAudio();
      
      aud.play()
    },
    async recordAudio() {

      var retaud = new Audio();
      //credits: https://medium.com/@bryanjenningz/how-to-record-and-play-audio-in-javascript-faa1b2b3e49b
      navigator.mediaDevices.getUserMedia({ audio: true }).then((stream) => {
        const mediaRecorder = new MediaRecorder(stream);
        mediaRecorder.start();

        const audioChunks = [];
        mediaRecorder.addEventListener("dataavailable", (event) => {
          audioChunks.push(event.data);
        });

        mediaRecorder.addEventListener("stop", () => {
          const audioBlob = new Blob(audioChunks);
          const audioUrl = URL.createObjectURL(audioBlob);
          const audio = new Audio(audioUrl);
          audio.play();
          retaud = audio
        });

        setTimeout(() => {
          mediaRecorder.stop();
        }, 3000);

      });

      return retaud;
    },
  },
  data() {
    return {
      headers: {
        Author: "SR",
      },
      showButton: {
        start: true,
        retry: true,
        confirm: true,
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

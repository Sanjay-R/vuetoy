<template>
    <button @click="onClick()" class="button">
        {{text}}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: {
            type: String,
            default: "default button"
        },
        button_color: {
            type: String,
            default: "#20b2aa"
        },
        action: String,
    },
    methods: {
        onClick() {
            console.log("button clicked", this.text);
            if(this.action == "record") {
                console.log("record audio!!")
            }
        },
    },
    data() {
        //https://www.infoq.com/news/2021/02/vue-3-css-variable-templating/
        //https://michaelnthiessen.com/vue-props-vs-data/
        //https://github.com/vuejs/rfcs/pull/231
        return {
            colord: this.button_color
        }
    },
}
</script>

<style scoped>
.button {
  background-color: white; 
  border: 2px solid v-bind(colord); /*CHANGE TO INPUT COLOR */
  border-radius: 10%;
  color: black;
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
}

.button:hover {
    background-color: v-bind(colord);
    color:white;
}
</style>
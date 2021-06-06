<template>
    <button :click="onClick()" class="button">
        {{text}}
    </button>
    <!-- <div>
        <style>
            :root {
                --clr : {{color}};
            }
        </style>
    </div> -->
    <!-- https://www.telerik.com/blogs/passing-variables-to-css-on-a-vue-component 
    https://stackoverflow.com/questions/47322875/vue-js-dynamic-style-with-variables
    -->
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
        }
    },
    methods: {
        onClick() {
            // this.$emit('button-clicked')
            console.log("button clicked");
        },
    },
    data() {
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
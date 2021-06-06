<template>
    <button v-bind:click="onClick()" :style="{background: color}" class="button">
        {{text}}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String,
    },
    methods: {
        onClick() {
            this.$emit('button-clicked')
        }
    }
}
</script>

<style lang="scss" scoped>

</style>
<template>
    <input :value="value" @input="updateInput" type="text">
</template>

<script>
    export default {
        name: 'my-input',

        props: {
            value: {
                type: [String, Number]
            }
        },

        methods: {
            updateInput(event) {
                this.$emit('update:value', event.target.value)
            }
        }
    }
</script>

<style scoped>
    
</style>
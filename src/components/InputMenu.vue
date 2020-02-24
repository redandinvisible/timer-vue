<template>
    <div>
        <input @keyup.enter="onInput"/>
    </div>
</template>

<script>
    export default {
        name: "InputMenu",
        methods: {
            onInput: function (event) {
                this.$emit("timeSubmit", event.target.value)
            }
        }
    }
</script>

<style scoped>
    div {
        margin: 20px
    }
</style>
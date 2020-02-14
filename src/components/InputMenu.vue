<template>
    <div>
        <input @input="onInput"/>
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

</style>
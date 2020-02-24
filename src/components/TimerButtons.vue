<template>
    <div class="row">
        <div @click="onClick($event)" value="play"><img :src="'./images/play.svg'" id="play" width="50" height="50"></div>
        <div @click="onClick($event)" value="pause"><img :src="'./images/pause.svg'" id="pause" width="50" height="50"></div>
        <div @click="onClick($event)" value="startover"><img :src="'./images/start-over.svg'" id="startover" width="50" height="50"></div>
    </div>
</template>

<script>
    export default {
        name: "TimerButtons",
        methods: {
            onClick(e) {
                this.$emit('buttonClicked', e.target.id)
            }
        }
    }
</script>

<style scoped>

</style>
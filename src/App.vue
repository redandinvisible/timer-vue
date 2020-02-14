<template>
    <div>
        <InputMenu @timeSubmit="onTimeSubmit"/>
        <Timer :time_pattern="timePattern"/>
    </div>
</template>

<script>
    import Timer from './components/Timer';
    import InputMenu from './components/InputMenu';

    export default {
        name: "App",
        components: {
            Timer,
            InputMenu
        },
        data() {
            return {
                timePattern: ""
            };
        },
        methods: {
            onTimeSubmit(timePattern) {
                this.timePattern = timePattern
            }
        }
    };
</script>
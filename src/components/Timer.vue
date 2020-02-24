<template>
    <div>
        <div id="counter-wrapper">
            <div class="col-xs-12">
                <div id="timer" class="timer-undertime">
                    <div id="counter-container" class="row">
                        <div>{{ minutes }}</div>
                        <div>:</div>
                        <div>{{ seconds }}</div>
                    </div>
                </div>
            </div>
        </div>
        <TimerButtons @buttonClicked="onTimerButtonClicked"/>
    </div>
</template>

<script>
    import TimerButtons from "./TimerButtons";

    export default {
        name: "Timer",
        components: {
            TimerButtons
        },
        props: {
            time_pattern: String
        },
        data() {
            return {
                minutes: "",
                seconds: ""
            }
        },
        watch: {
            time_pattern: {
                handler(pattern) {
                    let vals = pattern.split(":").reverse();
                    this.minutes = vals[1];
                    this.seconds = vals[0];
                }
            }
        },
        methods: {
            onTimerButtonClicked(id) {
                switch(id) {
                    case 'play':
                        this.startCountdown();
                        break;
                    case 'pause':
                        this.pauseCountdown();
                        break;
                    case 'startover':
                        this.restartCountdown();
                        break;
                }
            },
            startCountdown() {
                // eslint-disable-next-line no-console
                return console.log("startCountdown");
            },
            pauseCountdown() {
                // eslint-disable-next-line no-console
                return console.log("pauseCountdown");
            },
            restartCountdown() {
                // eslint-disable-next-line no-console
                return console.log("restartCountdown");
            },
            timesUp() {
                // eslint-disable-next-line no-console
                return console.log("time's up!");
            }
        }
    };
</script>

<style scoped>
    #counter-wrapper {
        font-family: "Helvetica Monospaced W01", "Lucida Console", Monaco, monospace;
        color: #ffab00;
        font-size: 50vmin;
        display: flex;
        justify-content: center
    }

</style>
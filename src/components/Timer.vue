<template>
    <div class="content">
        <div class="counter-wrapper">
            <div class="col-xs-12">
                <div id="timer" class="timer-undertime">
                    <div id="counter-container" class="row">
                        <div>{{ minutes }}</div>
                        <div>:</div>
                        <div>{{ seconds | LpadSeconds }}</div>
                    </div>
                </div>
            </div>
        </div>
        <TimerButtons @buttonClicked="onTimerButtonClicked"/>
    </div>
</template>

<script>
    import TimerButtons from "./TimerButtons";
    import {mixin as VueTimers} from 'vue-timers'
    import {modulo_seconds} from "../util/number";
    import LpadSeconds from '../filters/LpadSeconds';

    let one_second = 1000;

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
                seconds: "",
            }
        },
        mixins: [VueTimers],
        timers: {
            countdown: { time: one_second, repeat: true }
        },
        filters: {
            LpadSeconds
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
                this.$timer.start('countdown');
            },
            pauseCountdown() {
                this.$timer.stop('countdown');
            },
            restartCountdown() {
                // eslint-disable-next-line no-console
                return console.log("restartCountdown");
            },
            timesUp() {
                // eslint-disable-next-line no-console
                return console.log("time's up!");
            },
            countdown() {
                this.seconds = modulo_seconds(this.seconds - 1);
                if (this.seconds == 59 && this.minutes > 0) {
                    this.minutes -= 1;
                }
                if (this.seconds == 0 && this.minutes == 0) {
                    this.$timer.stop('countdown');
                }
            }
        }
    };
</script>

<style scoped>
    .counter-wrapper {
        font-family: "Helvetica Monospaced W01", "Lucida Console", Monaco, monospace;
        color: #ffab00;
        font-size: 50vmin;
        display:flex;
        justify-content: center;
        align-items: center;
        height: 90vh;
    }
    .content {
        height: 100vh;
    }

</style>
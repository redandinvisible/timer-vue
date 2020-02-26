<template>
    <div class="container-fluid">
        <InputMenu v-show="displayTimeInput" @timeSubmit="onTimeSubmit"/>
        <Timer v-show="!displayTimeInput" :time_pattern="timePattern"/>
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
                timePattern: "",
                displayTimeInput: true
            };
        },
        methods: {
            onTimeSubmit(timePattern) {
                this.timePattern = timePattern;
                this.displayTimeInput = false;
            }
        }
    };
</script>

<style>
    html, body {
        background-color: black;
        height: 100vh;
    }
    .container-fluid {
        background-color: black;
        height: 100vh;
        margin: 0;
    }
    @font-face {
        font-family: "Neue Helvetica W01";
        src: url("/fonts/c07fef9e-a934-42d7-92ad-69205f2b8a00.eot?#iefix");
        src: url("/fonts/c07fef9e-a934-42d7-92ad-69205f2b8a00.eot?#iefix") format("eot"), url("/fonts/3b303641-706e-4221-94c4-4fb491f4f8ef.woff2") format("woff2"), url("/fonts/14ff6081-326d-4dae-b778-d7afa66166fc.woff") format("woff"), url("/fonts/8fda1e47-19be-46c7-8d83-8d4fb35572f0.ttf") format("truetype"), url("/fonts/f751c8ae-1057-46d9-8d74-62592e002568.svg#f751c8ae-1057-46d9-8d74-62592e002568") format("svg");
        font-weight: 600;
        font-style: normal
    }
    @font-face {
        font-family: "Helvetica Monospaced W01";
        src: url("/fonts/87f6a1c1-d634-4755-be60-566164ea2dc4.eot?#iefix");
        src: url("/fonts/87f6a1c1-d634-4755-be60-566164ea2dc4.eot?#iefix") format("eot"), url("/fonts/9d82d212-4c22-4991-8c6d-3c4e521c0351.woff2") format("woff2"), url("/fonts/bb9c8441-1fde-4ac4-aa47-c866378b30f6.woff") format("woff"), url("/fonts/a8b10911-4e7a-4536-b925-3684e4014a42.ttf") format("truetype"), url("/fonts/27aa95f2-938d-43aa-8d23-d3cd6316c460.svg#27aa95f2-938d-43aa-8d23-d3cd6316c460") format("svg");
        font-weight: 400;
        font-style: normal
    }
</style>
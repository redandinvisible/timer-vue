<template>
    <div>
         {{ time_pattern }}
    </div>
</template>

<script>
    export default {
        name: "Timer",
        props: {
            time_pattern: String
        }
    };
</script>

<style scoped>

</style>
<script setup>
    import { ref } from 'vue'

    let seconds = ref(0)
    let minutes = ref(0)
    let hours = ref(0)

    function getTime() {
        let time = new Date()

        seconds.value = time.getSeconds().toString().padStart(2, "0")
        minutes.value = time.getMinutes().toString().padStart(2, "0")
        hours.value = time.getHours().toString().padStart(2, "0")

        document.title = `${hours.value}:${minutes.value}:${seconds.value}`
    }

    setInterval(() => {
        getTime()
    }, 1000)

    getTime()
</script>

<template>
    <p><span id="hours">{{ hours }}</span>:<span id="minutes">{{ minutes }}</span>:<span id="seconds">{{ seconds }}</span></p>
</template>

<style scoped>
    p {
        font-variant-numeric: tabular-nums;
        margin: 7rem 0 7rem 0;
        font-size: 80px;
        text-align: center;
        font-weight: 500;
    }
</style>

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
    <div id="wrapper">
        <div id="clock-wrapper">
            <p><span id="hours">{{ hours }}</span>:<span id="minutes">{{ minutes }}</span>:<span id="seconds">{{ seconds }}</span></p>
        </div>
    </div>
</template>

<style scoped>
    #wrapper {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 40px;
    }

    #clock-wrapper {
        border-width: 1px;
        border-style: solid;
        border-color: #3d3d3d;
        width: fit-content;
        padding: 15px 30px 15px 30px;;
    }

    p {
        font-variant-numeric: tabular-nums;
        font-size: 2.25rem;
        font-weight: 500;
    }
</style>

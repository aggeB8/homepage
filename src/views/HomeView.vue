<script setup>
    //splitta en entry till flera och gör de till local
    import router from '../router'

    let links = JSON.parse(localStorage.getItem('links'))
</script>

<template>
    <button @click="router.push('/createlink')">Create a new link</button>
    <div v-for="link in links">
        {{ link }}
    </div>

    <p style="opacity: 0.1;">Drag n drop för att arrangera lista över länkar</p>
</template>

<style scoped>
    button {
        width: 100%;
    }
</style>
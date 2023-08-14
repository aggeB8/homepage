<script setup>
    //splitta en entry till flera och gör de till local
    import router from '../router'
</script>

<template>
    <button @click="router.push('/createlink')">Create a new link</button>
    <button @click="router.push('/sortlinks')">Sort links</button>
    <button @click="router.push('/themes')">Theming</button>
</template>

<style scoped>
    button {
        width: 100%;
        height: 2rem;
    }
    
    button:not(:last-child) {
        margin-bottom: 1rem;
    }
</style>
<script setup>
    //splitta en entry till flera och gör de till local
    import { ref } from 'vue'

    import router from '../router'

    let linkArray = ref(JSON.parse(localStorage.getItem('links')))

    function deleteLink(link) {
        let deleteIndex = linkArray.value.indexOf(link)

        linkArray.value.splice(deleteIndex, 1)
        localStorage.setItem('links', JSON.stringify(linkArray.value))
    }
</script>

<template>
    <button @click="router.push('/createlink')">Create a new link</button>
    <div v-for="link in linkArray">
        <i @click="deleteLink(link)" :class="link.linkIcon"></i>
        <p>edit</p>
    </div>

    <p style="opacity: 0.1;">Drag n drop för att arrangera lista över länkar<br>Sortera med IDS! lägg till de i localstorage</p>
</template>

<style scoped>
    button {
        width: 100%;
    }
</style>
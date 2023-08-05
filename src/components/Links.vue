<script setup>
    import { ref } from 'vue'

    let linkArray = ref(JSON.parse(localStorage.getItem('links')))

    function goTo(site) {
        window.open(site, '_blank');
    }
</script>

<template>
    <div id="grid">
        <div @click="goTo(link.linkURL)" class="grid-item" v-for="link in linkArray">
            <i :class="link.linkIcon"></i>
        </div>
    </div>
</template>

<style scoped>
    #grid {
        display: flex;
        gap: 2rem;
        flex-direction: row;
        justify-content: center;
    }

    .grid-item {
        width: 100px;
        height: 100px;

        text-align: center;
        line-height: 100px;
        font-size: 2rem;
        border-radius: 20px;
        transition: 0.15s;
        cursor: pointer;

        border: 1px solid var(--border-color);
    }

    .grid-item:hover {
        background-color: rgb(67, 139, 139);

        
    }
</style>

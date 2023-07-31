<script setup>
    import { ref } from 'vue'
    import { RouterLink } from 'vue-router'
    let links = ref([
        { site: "https://www.youtube.com", icon: "bi bi-youtube" },
        { site: "https://www.github.com", icon: "bi bi-github" },
        { site: "https://www.steamcommunity.com", icon: "bi bi-steam" },
    ])

    function goTo(site) {
        window.open(site, '_blank');
    }
</script>

<template>
    <div id="grid">
        <div @click="goTo(link.site)" class="grid-item" v-for="link in links">
            <i :class="link.icon"></i>
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
        width: 200px;
        height: 200px;
        background-color: var(--sec-color);
        text-align: center;
        line-height: 200px;
        font-size: 80px;
        border-radius: 20px;
        transition: 0.15s;
        cursor: pointer;
    }

    .grid-item:hover {
        background-color: rgb(67, 139, 139);
    }

</style>

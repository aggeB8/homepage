<script setup>
    //splitta en entry till flera och gör de till local
    import { ref } from 'vue'
    import router from '../router'

    let linkArray = ref(JSON.parse(localStorage.getItem('links')))

    function linkIndex(link) {
        return linkArray.value.indexOf(link)
    }

    function deleteLink(link) {
        let index = linkIndex(link)
        linkArray.value.splice(index, 1)
        localStorage.setItem('links', JSON.stringify(linkArray.value))
    }

    function moveLinkUp(link) {
        let index = linkIndex(link)
        if (index > 0) {
            linkArray.value.splice(index, 1)
            linkArray.value.splice(index-1, 0, link)
            localStorage.setItem('links', JSON.stringify(linkArray.value))
        }
    }

    function moveLinkDown(link) {
        let index = linkIndex(link)
        linkArray.value.splice(index, 1)
        linkArray.value.splice(index+1, 0, link)
        localStorage.setItem('links', JSON.stringify(linkArray.value))
    }
</script>

<template>
    <div id="links">
        <div class="link" v-for="link in linkArray">
            <div class="sort-order">
                <i @click="moveLinkUp(link)" class="bi bi-arrow-bar-up"></i>
                <i @click="moveLinkDown(link)" class="bi bi-arrow-bar-down"></i>
            </div>

            <i id="icon" :class="link.linkIcon"></i>
            <p @click="deleteLink(link)">delete</p>
        </div>
    </div>
</template>

<style scoped>
    p {
        cursor: pointer;
    }

    .sort-order > i {
        cursor: pointer;
    }

    #icon {
        font-size: var(--icon-size);
    }

    button {
        width: 100%;
        margin-bottom: 1rem;
    }

    #links {
        width: 100%;
    }

    .link {
        align-items: center;
        display: flex;
        flex-direction: col;
        gap: 1rem;
        border: 1px solid var(--border-color);
        border-radius: var(--border-radius);
        padding: 20px;
    }

    .link:not(:last-child) {
        margin-bottom: 1rem;
    }

    .sort-order {
        display: flex;
        flex-direction: column;
    }

    .sort-order > i {
        font-size: 20px;
    }
</style>
<script setup>
    import { ref } from 'vue'
    import { iconArray } from '../composables/iconArray'

    import router from '../router'
    let searchTerm = ref()

    let filteredIcons = ref(iconArray)

    function searchIcons(searchTerm) {
        let arr = iconArray
        let searchResult = arr.filter(icon => icon.match(searchTerm))
        filteredIcons.value = searchResult
    }

    let linkURL = ref()
    let linkIcon = ref()

    function setIcon(icon) {
        linkIcon.value = icon
    }

    function createLink() {
        if (linkURL.value === '' || linkURL.value === undefined || linkIcon.value === undefined) {
            console.log('displaya errormeddelande')
        } else {
            let linkArray = JSON.parse(localStorage.getItem('links'))
            linkArray.push({linkIcon: linkIcon.value, linkURL: linkURL.value})
            localStorage.setItem('links', JSON.stringify(linkArray))
            router.push('/')
            window.location.reload() //fixa bättre 'vue' metod
        }
    }
</script>

<template>
    <div id="wrapper">
        <input v-model="linkURL" placeholder="Website URL">
        <input id="icon-input" @keyup="searchIcons(searchTerm)" placeholder="Search icons" maxlength="15" v-model="searchTerm">
        <button @click="createLink">Create link</button>

        <div id="icon-menu">
            <div class="icon-wrapper" v-for="icon in filteredIcons" @click="setIcon(icon)">
                <i class :class="icon"></i>
            </div>
        </div>
    </div>
</template>

<style scoped>
    input {
        margin-bottom: 10px;
    }

    button {
        width: 50%;
    }

    #wrapper {
        width: 260px
    }

    #icon-input {
        width: 50%;
    }

    #icon-menu {
        width: 260px;
        height: 260px;
        overflow: scroll;
        display: flex;
        flex-wrap: wrap;
        align-content: flex-start;
        justify-content: space-between;
    }

    .icon-wrapper {
        font-size: 1.7rem;
        border: 1px solid var(--border-color);
        border-radius: 10px;
        width: 32%;
        height: 32%;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: 0.2s;
        margin-bottom: 2%;
        cursor: pointer;
    }

    .icon-wrapper:hover {
        background-color: rgb(52, 52, 52);
    }
</style>

<script setup>
import { ref } from 'vue'
import { iconArray } from '../composables/iconArray'

let filteredIcons = ref(iconArray)

function searchIcons(searchTerm) {
    let arr = iconArray
    let searchResult = arr.filter(icon => icon.match(searchTerm))
    filteredIcons.value = searchResult
    console.log(filteredIcons)
}
</script>

<template>
    <div id="wrapper">
        <div class="input-wrapper">
            <input @keyup="searchIcons(searchTerm)" placeholder="Search icons" maxlength="15" v-model="searchTerm">
        </div>
        <div id="icon-menu">            
            <div class="icon-wrapper" v-for="icon in filteredIcons">
                <i class :class="icon"></i>
            </div>
        </div>
    </div>
</template>

<style scoped>
    #wrapper {
        width: 260px
    }

    .input-wrapper {
        margin-top: 10px;
        margin-bottom: 10px;
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
        font-size: 2.5rem;
        background-color: var(--sec-color);
        border-radius: 10px;
        width: 32%;
        height: 32%;
        display: flex;
        justify-content: center;
        align-items: center;
        transition: 0.2s;
        margin-bottom: 2%;
    }

    .icon-wrapper:hover {
        background-color: rgb(52, 52, 52);
    }


</style>
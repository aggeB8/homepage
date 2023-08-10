<script setup>
    import { onKeyStroke } from '@vueuse/core'
    import { ref } from 'vue'

    let searchString = ref()

    onKeyStroke((e) => {
        const searchbar = document.querySelector('#searchbar')
        
        if (!modal.open) {
            switch(e.key) {
                case 'Enter':
                    if (searchbar.open) {
                        window.open(`http://www.google.com/search?q=${searchString.value}`, '_blank');
                        break
                    }
                case 'Escape':
                    break
                default:
                    searchbar.showModal()
            }
        }
    })
</script>

<template>
    <dialog id="searchbar">
        <input v-model="searchString" type="text" name="" id="">
    </dialog>
</template>

<style scoped>
    input {
        font-size: 2rem;
        width: 400px;
    }
    
    #searchbar {
        background-color: #00000000;
        border: none;
        top: 20%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    #searchbar::backdrop {
        background-color: rgba(0, 0, 0, 0.757);
    }
</style>
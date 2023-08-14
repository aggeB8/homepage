<script setup>
    import router from '../router'
    function openModal() {
        const modal = document.querySelector('#modal')
        modal.showModal()
    }

    function closeModal() {
        const modal = document.querySelector('#modal')
        modal.close()
        router.push('/')
    }
</script>

<template>
    <i id="gear" @click="openModal" class="bi bi-gear"></i>
    <dialog id="modal">
        <header>
            <i @click="router.push('/')" id="return-button" class="bi bi-arrow-return-left"></i>
            <p>Configure</p>
            <i @click="closeModal" id="close-button" class="bi bi-x-lg"></i>
        </header>
        <div id="modal-container">
            <RouterView />
        </div>
    </dialog>
</template>

<style scoped>
    i {
        cursor: pointer;
    }
    
    #gear {
        font-size: 1.5rem;
        position: absolute;
        right: 1rem;
        margin-top: 1rem;
        color: rgba(255, 255, 255, 0.259);
        transition: 0.25s;
    }

    #gear:hover {
        color: rgb(255, 255, 255)
    }

    #modal {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 300px;
        height: fit-content;
        border: none;
        /* background-color: var(--bg-color); */
        background-color: var(--modal-bg);

        border-radius: 10px;
        border-width: 1px;
        border-style: solid;
        border-color: var(--border-color);
    }

    #modal::backdrop {
        background-color: rgba(0, 0, 0, 0.5);
    }

    header {
        width: 100%;
        height: 3rem;
        background-color: var(--modal-bg-header);
        backdrop-filter: var(--modal-bg-blur);
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 1rem;
        font-weight: 500;

        border-bottom-width: 1px;
        border-bottom-style: solid;
        border-color: var(--border-color);
    }

    #return-button {
        position: absolute;
        left: 1rem;
        top: 1rem;
    }

    #close-button {
        position: absolute;
        right: 1rem;
    }

    #modal-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 1rem;
    }


</style>
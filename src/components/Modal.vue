<script setup>
    import IconPicker from '../components/IconPicker.vue'

    function openModal() {
        const modal = document.querySelector('#modal')
        modal.showModal()
    }

    function closeModal() {
        const modal = document.querySelector('#modal')
        modal.close()
    }
</script>

<template>
    <i id="gear" @click="openModal" class="bi bi-gear"></i>

    <dialog id="modal">
        <header>
            <p>Konfigurera</p>
            <i @click="closeModal" class="bi bi-x-lg"></i>
        </header>
        <div id="modal-container">
            <p style="opacity: 0.1;">Färg<br>Länkar(crud ICONPICKER, drag n drop för order!)</p>
            <IconPicker />
        </div>

    </dialog>

</template>

<style scoped>
    #gear {
        font-size: 3rem;
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
        border-radius: 10px;
        background-color: var(--bg-color);
    }

    #modal::backdrop {
        background-color: rgba(0, 0, 0, 0.656)
    }

    header {
        width: 100%;
        height: 3rem;
        background-color: var(--sec-color);
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 20px;
        font-weight: 500;
    }

    header > i {
        position: absolute;
        right: 1rem;
    }

    #modal-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 1rem
    }


</style>
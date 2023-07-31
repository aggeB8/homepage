<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import Links from './components/Links.vue'
  import Clock from './components/Clock.vue'
  import Modal from './components/Modal.vue'

  if (localStorage.getItem('links') === null) {
    localStorage.setItem('links', '[]')
  }
</script>

<!--
  <RouterView />
-->

<template>
  <main>
    <Modal />
    <Clock />
    <Links />

    <footer>

    </footer>
  </main>
</template>

<style scoped>
  main {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  footer {
    text-align: center;
    margin-top: auto;
    text-decoration: none;
  }

</style>

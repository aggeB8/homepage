<script setup>
  import Links from './components/Links.vue'
  import Clock from './components/Clock.vue'
  import Modal from './components/Modal.vue'
  import Searchbar from './components/Searchbar.vue'

  if (localStorage.getItem('links') === null) {
    localStorage.setItem('links', '[]')
  }
</script>

<!--
  <RouterView />
-->

<template>
  <Modal />
  <main>
      <Clock />
      <Searchbar />
      <Links />
  </main>
</template>

<style scoped>
  main {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

</style>

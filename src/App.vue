<script setup>
  import { RouterLink, RouterView } from 'vue-router'
  import Clock from './components/Clock.vue'
  import Modal from './components/Modal.vue'
</script>

<template>
  <main>
    <Modal />
    <Clock />
    <RouterView />

    <footer>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
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

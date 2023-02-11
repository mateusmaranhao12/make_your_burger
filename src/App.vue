<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view/>
</template>

<script>

  import Navbar from './components/Navbar.vue'

  export default {
    components: {
      Navbar
    },

    data() {
      return {
        logo_src: '/img/logo.png',
        app_name: 'Make Your Burger'
      }
    }
  }
</script>

<style lang="scss">
    @import '@/scss/index';
</style>
<template>
    <div id="nav">
        <router-link id="logo-url" to="/">
            <img :src="logo" :alt="alt" id="logo" />
        </router-link>
        <router-link to="/">Home</router-link> |
        <router-link to="/pedidos">Pedidos</router-link>
    </div>
</template>

<script>
    export default {
        name: 'Navbar',
        props: ['logo', 'alt']
    }
</script>

<style lang="scss">
    @import '@/scss/index';
</style>
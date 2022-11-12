<template>
    <div id="nav" >
        <RouterLink to="/">
            <img src="" id="logo">
        </RouterLink>
        <router-link to="/">Home</router-link> |
        <router-link to="/pedidos">Pedidos</router-link>
    </div>
</template>

<script>
    export default {
        name:'Navbar',
        data(){
            return {

            }
        }
    }
</script>

<style scoped>

</style>
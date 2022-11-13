<template>
    <div id="nav" >
        <router-link to="/">
            <img src="" id="logo">
        </router-link>
        <router-link to="/">Home</router-link> | <!--Estabelece o link com o componente home atráves desse "to="/"" que referencia ao path de home, isso é definido dentro da pasta Router-->
        <router-link to="/pedidos">Pedidos</router-link> <!--Estabelece o link com o componente Pedidos atráves do "to=" que referencia ao path de Pedidos, definido dentro da pasta Router-->
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
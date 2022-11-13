<template>
    <div id="nav" >
        <router-link to="/" id="logo-url">
            <img :src="logo" :alt="alt" id="logo">
        </router-link>
        <router-link to="/">Home</router-link>  <!--Estabelece o link com o componente home atráves desse "to="/"" que referencia ao path de home, isso é definido dentro da pasta Router-->
        <router-link to="/pedidos">Pedidos</router-link> <!--Estabelece o link com o componente Pedidos atráves do "to=" que referencia ao path de Pedidos, definido dentro da pasta Router-->
    </div>
</template>

<script>
    export default {
        name:'Navbar',
        props: ["logo", "alt"],
        data(){
            return {

            }
        }
    }
</script>

<style scoped>
    #nav{
        background-color: #222;
        border-bottom: 4px solid #111;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    #nav #logo-url{
        margin: auto;
        margin-left: 0;
    }

    #logo{
        width: 40px;
        height: 40px;
    }

    #nav a {
        color: #FCBA03;
        text-decoration: none;
        margin: 12px;
        transition: .5s;
    }

    #nav a:hover {
        color: white
    }
</style>
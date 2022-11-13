<template>
  <div>
    <Navbar :logo="logo_src" :alt="app_name" /> <!--Importa o componete de Navbar que contém os links definidos com o VueRouter/ Adcionando a logo atrávez de props para a Navbar-->
    <router-view/> <!--A view é feita através desse componente aqui, ou seja os outros componentes podem ser repetidos por estarem fora dessaa tag -->
    <Footer />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';

  export default {
    name:'App',
    components:{
      Navbar,
      Footer
    },
    data() {
      return {
        logo_src: "/img/logo.png",
        app_name: "Make Your burger"
      }
    }
  }
</script>

<style>
  *{ /*Aqui organiza a estilização global do site, vai pegar todo o conteudo que não está dentro de uma div definindo uma estilização padrão*/
    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  .main-container{ /*Aqui para evitar ter que alterar dentro de Nav e Footer utiliza a style global, ja alterando as duas ao mesmo tempo */
    margin: 50px;
    min-height: 250px;
  }

  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }
</style>

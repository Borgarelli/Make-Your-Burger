<template>
  <div>
    <Navbar /> <!--Importa o componete de Navbar que contém os links definidos com o VueRouter-->
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

      }
    }
  }
</script>

<style>

</style>

<template>
  <div>
    <Navbar />
  </div>
   <router-view/> <!--A view é feita através desse componente aqui, ou seja os outros componentes podem ser repetidos por estarem fora dessaa tag -->
  <Footer />
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

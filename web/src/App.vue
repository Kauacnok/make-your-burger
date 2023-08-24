<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view/>    
  <Footer />
</template>

<script>
  import Navbar from './components/Navbar'
  import Footer from './components/Footer'
  export default {
    data() {
      return {
        logo_src: "/assets/logo.png",
        app_name: "Make Your Burger"
      }
    },
    components: {
      Navbar,
      Footer
    }
  }
</script>
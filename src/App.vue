<template>
  <Meta/>
  <Navbar/>
  <Header/>
  <Github/>
  <Projects/>
  <ContactForm/>
</template>

<script>
  import ContactForm from './components/ContactForm.vue'
  import Meta from './components/Meta.vue'
  import Navbar from './components/Navbar.vue'
  import Github from './components/Github.vue'
  import Header from './components/Header.vue'
  import Projects from './components/Projects.vue'

  export default {
    name: 'App',
    components: {
      ContactForm,
      Meta,
      Navbar,
      Github,
      Header,
      Projects
    }
  }
</script>

<style lang="scss">
  @font-face {
    font-family: "Avenir Next";
    src: url('./assets/fonts/AvenirNextLTPro-Regular.otf');
  }

  @font-face {
    font-family: "Avenir Next Bold";
    src: url('./assets/fonts/AvenirNextLTPro-Bold.otf');
  }

  b,
  strong,
  .brand,
  a {
    font-family: Avenir Next Bold;
  }

  html {
    scroll-behavior: smooth;
    max-width: 1140px;
    margin: 0 auto;
    width: 100%;
    padding: 40px 40px 0px 40px;
  }

  body {
    padding-top: 40px;
  }

  h1,
  h2,
  h3 {
    font-family: Avenir Next Bold;
  }

  p {
    font-family: Avenir Next;
  }

  h1 {
    font-weight: 700;
    font-size: 50px;
  }

  h2 {
    font-weight: 700;
    font-size: 45px;
    margin-bottom: 40px;
    text-align: center;
  }

  h3 {
    font-weight: 700;
    font-size: 25px;
  }
</style>

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
  html {
    scroll-behavior: smooth;
    margin: 0 auto;
    width: 100%;
  }

  body {
    background-color: $background;
    color: $grey;
    font-family: 'Ubuntu', sans-serif;
    font-size: 20px;
    line-height: 28px;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    font-family: 'Ubuntu', sans-serif;
    font-weight: bold;
    color: $grey;
    margin-bottom: 0;
  }

  h1 {
    color: $orange;
    font-size: 64px;
    line-height: 83px;
  }

  h2 {
    font-size: 36px;
    line-height: 41px;
  }

  h3 {
    font-weight: 700;
    font-size: 25px;
  }

  h6 {
    margin-bottom: 0;
    font-size: 24px;
    line-height: 28px;
  }

  em {
    font-style: normal;
    color: $white;
    font-weight: bold;
  }

  b,
  strong {
    color: $orange;
    text-transform: uppercase;
  }

  footer {
    text-align: center;
    padding: 20px;
  }
</style>

<template>
  <Meta/>
  <Navbar/>
  <Header/>
  <Github/>
  <Projects/>
  <ContactForm/>

  <footer>
    Copyright 2021 | All Rights Reserved
  </footer>
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
  b,
  strong,
  em,
  .brand,
  .toptitle,
  .subtitle,
  .btn,
  .badge,
  a {
    font-family: 'Ubuntu', sans-serif;
  }

  em {
    font-style: normal;
    color: $white;
  }

  strong {
    color: $orange;
    text-transform: uppercase;
  }

  body {
    background-color: $background;
  }

  html {
    scroll-behavior: smooth;
    max-width: 1140px;
    margin: 0 auto;
    width: 100%;
  }

  h1,
  h2,
  h3 {
    font-family: 'Ubuntu', sans-serif;
    color: $grey;
  }

  p {
    font-family: 'Ubuntu', sans-serif;
    color: $grey;
  }

  h1 {
    color: $orange;
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

  footer {
    color: $grey;
    text-align: center;
    padding: 20px;
  }
</style>

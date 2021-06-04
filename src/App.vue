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
  import hr from "@/assets/hr.svg";

  export default {
    name: 'App',
    components: {
      ContactForm,
      Meta,
      Navbar,
      Github,
      Header,
      Projects
    },
    data() {
      return {
        hr
      }
    }
  }
</script>

<style lang="scss">
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
    color: $white;
    font-size: 36px;
    line-height: 48px;
    margin-bottom: 10px;
    text-align: center;
  }

  h3 {
    font-weight: 700;
    color: $white;
    font-size: 30px;
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

  hr {
    height: 10px !important;
    background: url("~@/assets/hr.svg");
    background-repeat: no-repeat;
    background-position: center;
    margin-bottom: 20px;
    margin-top: 0;
    opacity: 1;
    border: 0;
    width: 100%;
  }

  .subtitle {
    font-size: 24px;
    font-weight: bold;
    margin: 0 0 3px;
    color: $orange;
    text-align: center;
  }

  .text {
    margin-bottom: 40px;
    text-align: center;

    @media (min-width: 992px) {
      margin-bottom: 80px;
    }
  }

  footer {
    text-align: center;
    padding: 20px;
  }
</style>

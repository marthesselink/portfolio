<template>
  <Meta/>
  <Header/>
  <Github/>
  <RecentProjects/>
</template>

<script>
  import Meta from './components/Meta.vue'
  import Github from './components/Github.vue'
  import Header from './components/Header.vue'
  import RecentProjects from './components/RecentProjects.vue'

  export default {
    name: 'App',
    components: {
      Meta,
      Github,
      Header,
      RecentProjects
    }
  }
</script>

<style lang="scss">
  html {
    scroll-behavior: smooth;
    max-width: 1140px;
    margin: 0 auto;
    width: 100%;
    padding: 40px 40px 60px 40px;
  }

  h1,
  h2,
  h3 {
    font-family: Avenir Next;
    font-weight: bold;
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
  }

  h3 {
    font-weight: 700;
    font-size: 25px;
  }
</style>

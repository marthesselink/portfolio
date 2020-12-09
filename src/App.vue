<template>
  <Header/>

  <RecentProjects/>
</template>

<script>
  import Header from './components/Header.vue'
  import RecentProjects from './components/RecentProjects.vue'

  export default {
    name: 'App',
    components: {
      Header,
      RecentProjects
    }
  }
</script>

<style lang="scss">
  html {
    scroll-behavior: smooth;
  }

  h1 {
    font-weight: bold;
  }

  h2 {
    margin-bottom: 1rem;
  }

  h3 {
    font-size: 1.5rem;

    @media(min-width: 992px) {
      font-size: 2rem;
    }
  }
</style>

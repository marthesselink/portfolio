<template>
  <img alt="Vue logo" src="./assets/logo.png">

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

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  img {
    max-height: 150px;
  }
</style>

<template>
  <div class="header col-xs-12 p-2 p-md-3 text-center">
    <div v-if="page.title" class="align-middle">
      <h1 class="display-3">{{ page.title.rendered }}</h1>
      <p class="lead" v-html="page.content.rendered"></p>

      <img
        v-if="acfData"
        class="headerimage ml-auto"
        :src="acfData.headerImage"
        :srcset="acfData.headerImage + ' 1x,' +
          acfData.headerImage2x + ' 2x'"/>

        <p>This website is built with Vue.js with a Headless WP installation as backend. Interested in a site? Contact me!</p>

        <div v-if="acfData.linkedin" class="socials">
          <a class="btn btn-outline-secondary" :href="acfData.linkedin.url">Linkedin</a>
          <a class="btn btn-outline-secondary" :href="acfData.github.url">Github</a>
          <a class="btn btn-outline-secondary" :href="'mailto:' + acfData.mail">Mail</a>
        </div>

        <a href="#projects" class="btn viewproject btn-outline-primary" id="#link">Recent Projects</a>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Header',
    data() {
      return {
        pageUrl: "http://wp.marthesselink.nl/wp-json/wp/v2/pages?slug=home",
        page: [],
        acfUrl: "http://wp.marthesselink.nl/wp-json/acf/v3/pages/12",
        acfData: []
      };
    },
    methods : {
      getPageData() {
        axios
          .get(this.pageUrl)
          .then(response => {
            this.page = response.data[0];
            console.log('Page data retrieved!');
            console.log(this.page);
          })
          .catch(error => {
            console.log(error);
          });
      },
      getACFData() {
        axios
          .get(this.acfUrl)
          .then(response => {
            this.acfData = response.data.acf;
            console.log('ACF data retrieved!');
            console.log(this.acfData);
          })
          .catch(error => {
            console.log(error);
          });
      }
    },
    mounted() {
      this.getPageData();
      this.getACFData();
    }
  };
</script>

<style lang="scss" scoped>
  .header {
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .headerimage {
    max-width: 800px;
    width: 100%;
    margin-top: -2rem;

    @media(min-width: 520px) {
      margin-top: -3rem;
    }

    @media(min-width: 620px) {
      margin-top: -4rem;
    }

    @media(min-width: 840px) {
      margin-top: -5rem;
    }
  }

  .socials {
    .btn {
      margin: 1rem;
    }
  }

  .viewproject {
    width: 100%;
  }
</style>
